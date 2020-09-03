---
title: Co je nového v sadě Visual Studio 2019 SDK | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740396"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Co je nového v sadě Visual Studio 2019 SDK

Sada Visual Studio SDK obsahuje následující nové a aktualizované funkce pro sadu Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Upozornění synchronně autoloaded Extensions

Uživatelům se teď zobrazí upozornění, pokud se některá z jejich nainstalovaných rozšíření synchronně načítají při spuštění. Můžete se dozvědět více o upozornění na [synchronně autoloaded Extensions](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Jednotná, Sjednocená sada Visual Studio SDK

Všechny prostředky sady Visual Studio SDK teď můžete získat pomocí jediného balíčku NuGet [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Vylepšení registrace editoru

Od jejího vytvoření sada Visual Studio podporovala vlastní registraci editoru, kde editor může deklarovat své spřažení pro konkrétní rozšíření (například. XAML a. RC), nebo že je vhodný pro jakékoli rozšíření (. *). Počínaje verzí Visual Studio 2019 verze 16,1 rozšiřujeme podporu pro registraci editoru.

### <a name="filenames"></a>Názvy souborů

Kromě nebo místo registrace podpory pro konkrétní příponu souboru může editor zaregistrovat, že podporuje konkrétní názvy souborů, použitím nového `ProvideEditorFilename` atributu pro balíček editoru.

Například editor, který podporuje všechny soubory. JSON, použije tento `ProvideEditorExtension` atribut na jeho balíček:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Od 16,1, pokud MyEditor podporuje jenom několik dobře známých souborů. JSON, může místo toho použít tyto `ProvideEditorFilename` atributy na balíček:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Kontextu uicontexts

Editor může zaregistrovat jednu nebo více kontextu uicontexts, které reprezentují, když jsou povolené. Kontextu uicontexts jsou registrovány pomocí jedné nebo více instancí `ProvideEditorUIContextAttribute` balíčku, který registruje Editor.

Pokud editor zaregistroval kontextu uicontexts:

- Pokud je při otevření souboru s danou příponou aktivní aspoň jeden z jeho registrovaných kontextu uicontexts, je editor zahrnutý v editoru.
- Pokud není aktivní žádná z registrovaných kontextu uicontexts, Editor není zahrnutý do hledání v editoru.

Pokud editor neprovede registraci žádného kontextu uicontexts, je vždy zahrnut v editoru hledání této přípony.

Například pokud je editor k dispozici pouze v případě, že je otevřen projekt C#, může deklarovat toto spřažení použitím `ProvideEditorUIContext` atributu:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
