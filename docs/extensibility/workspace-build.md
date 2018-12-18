---
title: Pracovní prostor sestavení v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857631"
---
# <a name="workspace-build"></a>Pracovní prostor sestavení

Podpora sestavení [otevřít složku](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) scénáře vyžaduje zařízení extender k poskytování [indexované](workspace-indexing.md) a [kontextu souboru](workspace-file-contexts.md) data [pracovní prostor](workspaces.md), jako jako akci sestavení ke spuštění.

Tady je přehled, co bude potřebovat vaše rozšíření.

## <a name="build-file-context"></a>Vytvoření kontextu souboru

- Objekt pro vytváření zprostředkovatele
  - `ExportFileContextProviderAttribute` atribut s `supportedContextTypeGuids` ve všech příslušných `string` konstanty `BuildContextTypes`
  - Implementuje `IWorkspaceProviderFactory<IFileContextProvider>`
  - Poskytovatel kontextu souboru
    - Vrátit `FileContext` pro každé sestavení operace a podporované konfigurace
      - `contextType` z <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementuje <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> s `Configuration` vlastnosti, jako je konfigurace sestavení (třeba `"Debug|x86"`, `"ret"`, nebo `null` Pokud není k dispozici). Můžete také použít instanci <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Hodnota konfigurace **musí** odpovídat konfiguraci z hodnoty data z indexované souboru.

## <a name="indexed-build-file-data-value"></a>Hodnota dat souboru indexované sestavení

- Objekt pro vytváření zprostředkovatele
  - `ExportFileScannerAttribute` atribut s `IReadOnlyCollection<FileDataValue>` jako podporovaný typ.
  - Implementuje `IWorkspaceProviderFactory<IFileScanner>`
- Skener souboru na `ScanContentAsync<T>`
  - Vrací data při `FileScannerTypeConstants.FileDataValuesType` je argument typu
  - Vrací hodnotu data souboru pro každou konfiguraci zkonstruován pomocí:
    - `type` jako `BuildConfigurationContext.ContextTypeGuid`
    - `context` jako konfigurace sestavení (třeba `"Debug|x86"`, `"ret"`, nebo `null` Pokud není k dispozici). Tato hodnota **musí** odpovídat konfiguraci z kontextu souboru.

## <a name="build-file-context-action"></a>Akce kontextu souboru sestavení

- Objekt pro vytváření zprostředkovatele
  - `ExportFileContextActionProvider` atribut s `supportedContextTypeGuids` ve všech příslušných `string` konstanty `BuildContextTypes`
  - Implementuje `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Zprostředkovatel akce na `IFileContextActionProvider.GetActionsAsync`
  - Vrátí `IFileContextAction` , který odpovídá daný `FileContext.ContextType` hodnota
- Akce kontextu souboru
  - Implementuje `IFileContextAction` a <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Vrátí vlastnost `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` je `0x1000` pro sestavení, `0x1010` pro opakované sestavení, nebo `0x1020` pro vyčištění

>[!NOTE]
>Vzhledem k tomu, `FileDataValue` indexovat, je potřeba bude nějakou dobu mezi otevřete pracovní prostor a bod, ve kterém je soubor vyhledávat funkce úplného buildu. Zpoždění se projeví při prvním otevření složku, protože neexistuje žádný index uložené v mezipaměti.

## <a name="reporting-messages-from-a-build"></a>Vytváření sestav zprávy ze sestavení

Sestavení může přinášet informace, upozornění a chybové zprávy pro uživatele jedním ze dvou způsobů. Jednoduchým způsobem je použít <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> a zadejte <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, takto:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` a `BuildMessage.LogMessage` řídit chování ve kterém se zobrazí informace o uživateli. Žádné `BuildMessage.TaskType` hodnoty jiné než `None` dojde **seznam chyb** dané podrobnosti. `LogMessage` bude vždy výstupních v **sestavení** podokně **výstup** panelu nástrojů.

Můžete také rozšíření můžete přímo pracovat **seznam chyb** nebo **sestavení** podokně. Chybu existuje ve verzích před Visual Studio 2017 verze 15.7 kde `pszProjectUniqueName` argument <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> se ignoruje.

>[!WARNING]
>Volající `IFileContextAction.ExecuteAsync` můžete zadat libovolnou základní implementace pro `IProgress<IFileContextActionProgressUpdate>` argument. Nikdy vyvolat `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` přímo. Aktuálně neexistují žádné obecné pokyny pro používání tohoto argumentu, ale tato pravidla se můžou změnit.

## <a name="build-related-apis"></a>Rozhraní API související s sestavení

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> poskytuje podrobnosti o konfiguraci sestavení.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> ukazuje <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s uživatelům.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.vs.JSON a souboru launch.vs.json

Informace o vytváření souboru tasks.vs.json nebo souboru launch.vs.json najdete v tématu [přizpůsobení sestavení a ladění úloh](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Další kroky

* [Protokol jazyka serveru](language-server-protocol.md) – zjistěte, jak integrovat jazyk servery do sady Visual Studio.