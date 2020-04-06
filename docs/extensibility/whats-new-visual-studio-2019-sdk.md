---
title: Co je nového ve sadě Visual Studio 2019 SDK | Dokumenty společnosti Microsoft
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740396"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Co je nového v sadě Visual Studio 2019 SDK

Sada Visual Studio SDK obsahuje následující nové a aktualizované funkce pro Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Upozornění synchronně automaticky načtených rozšíření

Uživatelé se nyní zobrazí upozornění, pokud některý z jejich nainstalovaných rozšíření jsou synchronně automaticky načíst při spuštění. Další informace o upozornění na [synchronně automaticky načtené rozšíření](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Samostatná sada Visual Studio SDK

Nyní můžete získat všechny prostředky sady Visual Studio SDK prostřednictvím jednoho balíčku NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Vylepšení registrace editoru

Od svého vytvoření Visual Studio podporuje registraci vlastního editoru, kde editor může deklarovat jeho spřažení pro konkrétní rozšíření (například .xaml a .rc), nebo že je vhodný pro jakékoli rozšíření (.*). Počínaje Visual Studio 2019 verze 16.1, rozšiřujeme podporu pro registraci editoru.

### <a name="filenames"></a>Názvy souborů

Kromě nebo místo registrace podpory pro konkrétní příponu souboru může editor zaregistrovat, že `ProvideEditorFilename` podporuje konkrétní názvy souborů, použitím nového atributu na balíček editoru.

Například editor, který podporuje všechny soubory JSON, by tento `ProvideEditorExtension` atribut použil na svůj balíček:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Počínaje 16.1, pokud MyEditor podporuje pouze několik známých souborů JSON, `ProvideEditorFilename` může místo toho použít tyto atributy na svůj balíček:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Kontexty u

Editor můžete zaregistrovat jeden nebo více UIContexts, které představují, když je povolena. UIContexts jsou registrovány použitím jedné `ProvideEditorUIContextAttribute` nebo více instancí balíčku, který registruje editor.

Pokud editor zaregistroval UIContexts:

- Pokud alespoň jeden z jeho registrovaných UIContexts je aktivní při otevření souboru s danou příponou, editor je součástí hledání editoru.
- Pokud žádný z registrovaných UIContexts je aktivní, editor není součástí hledání editoru.

Pokud editor nezaregistruje žádné UIContexts, je vždy součástí hledání editoru pro toto rozšíření.

Například pokud editor je k dispozici pouze v případě, že je otevřen projekt jazyka `ProvideEditorUIContext` C#, může deklarovat tuto spřažení použitím atributu:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
