---
title: Sestavení pracovního prostoru v aplikaci Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553325"
---
# <a name="workspace-build"></a>Sestavení pracovního prostoru

Podpora sestavení ve scénářích [Otevřít složku](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) vyžaduje, aby zařízení rozšířilo data [indexovaných](workspace-indexing.md) a [souborových kontextů](workspace-file-contexts.md) pro [pracovní prostor](workspaces.md)a také akci sestavení ke spuštění.

Níže je uveden přehled toho, co vaše rozšíření bude potřebovat.

## <a name="build-file-context"></a>Kontext souboru sestavení

- Továrna poskytovatele
  - `ExportFileContextProviderAttribute` atribut s `supportedContextTypeGuids` jako všechny použitelné `string` konstanty z `BuildContextTypes`
  - Implementace `IWorkspaceProviderFactory<IFileContextProvider>`
  - Poskytovatel kontextu souboru
    - Vrátí `FileContext` pro každou operaci sestavení a podporu konfigurace.
      - `contextType` Výsledkem <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementuje <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> s `Configuration` vlastností jako konfigurací sestavení (například `"Debug|x86"` `"ret"` , nebo `null` Pokud není k dispozici). Alternativně můžete použít instanci <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . Hodnota konfigurace se **musí** shodovat s konfigurací z hodnoty indexovaných dat souboru.

## <a name="indexed-build-file-data-value"></a>Hodnota dat souboru indexovaného sestavení

- Továrna poskytovatele
  - `ExportFileScannerAttribute` atribut s `IReadOnlyCollection<FileDataValue>` jako podporovaný typ
  - Implementace `IWorkspaceProviderFactory<IFileScanner>`
- Skener souborů zapnut `ScanContentAsync<T>`
  - Vrátí data `FileScannerTypeConstants.FileDataValuesType` , pokud je argumentem typu.
  - Vrátí hodnotu dat souboru pro každou konfiguraci vytvořenou pomocí:
    - `type` formátu `BuildConfigurationContext.ContextTypeGuid`
    - `context` jako konfigurace sestavení (například `"Debug|x86"` `"ret"` , nebo `null` Pokud není k dispozici). Tato hodnota **musí** odpovídat konfiguraci z kontextu souboru.

## <a name="build-file-context-action"></a>Akce kontextu sestavení souboru

- Továrna poskytovatele
  - `ExportFileContextActionProvider` atribut s `supportedContextTypeGuids` jako všechny použitelné `string` konstanty z `BuildContextTypes`
  - Implementace `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Poskytovatel akcí na `IFileContextActionProvider.GetActionsAsync`
  - Vrátí `IFileContextAction` hodnotu, která odpovídá dané `FileContext.ContextType` hodnotě.
- Akce kontextu souboru
  - Implementuje `IFileContextAction` a <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` vlastnost vrací `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` je určen `0x1000` pro sestavení, `0x1010` pro opětovné sestavení nebo `0x1020` pro vyčištění

>[!NOTE]
>Vzhledem k tomu, že je `FileDataValue` nutné indexovat, dojde k určité době mezi otevřením pracovního prostoru a bodem, ve kterém je soubor prohledáván pro úplnou funkčnost sestavení. Zpoždění se zobrazí při prvním otevření složky, protože není k dispozici žádný index dříve v mezipaměti.

## <a name="reporting-messages-from-a-build"></a>Hlášení zpráv ze sestavení

Sestavení může pro uživatele surfovat informace, upozornění a chybové zprávy jedním ze dvou způsobů. Jednoduchý způsob je použít <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> a poskytnout <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> , například:

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

`BuildMessage.Type` a `BuildMessage.LogMessage` řídí chování, kde se uživatelům zobrazí informace. Jakákoli `BuildMessage.TaskType` jiná hodnota než `None` vytvoří položku **Seznam chyb** s danými podrobnostmi. `LogMessage` bude vždy výstup v podokně **sestavení** v okně **výstup** .

Alternativně mohou rozšíření pracovat přímo s **Seznam chyb** nebo pomocí podokna **sestavení** . Ve verzích starších než Visual Studio 2017 verze 15,7 existuje chyba, kde `pszProjectUniqueName` argument <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> je ignorován.

>[!WARNING]
>Volající `IFileContextAction.ExecuteAsync` mohou poskytnout libovolné základní implementace `IProgress<IFileContextActionProgressUpdate>` argumentu. Nikdy nevyvolat `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` přímo. Pro použití tohoto argumentu aktuálně nejsou k dispozici žádné obecné pokyny, ale tyto pokyny se mohou změnit.

## <a name="build-related-apis"></a>Související rozhraní API pro sestavení

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> poskytuje podrobnosti konfigurace sestavení.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> zobrazí <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> uživatele.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.jszapnuto a launch.vs.jsna

Informace o vytváření tasks.vs.jsnebo launch.vs.jsv souboru naleznete v tématu [přizpůsobení úloh sestavení a ladění](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Další kroky

* [Protokol jazykového serveru](language-server-protocol.md) – Naučte se integrovat jazykové servery do sady Visual Studio.