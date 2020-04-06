---
title: Rozšířit jazykovou službu pro podporu EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699588"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Podpora EditorConfig pro vaši jazykovou službu

[EditorConfig](https://editorconfig.org/) soubory umožňují popsat běžné možnosti textového editoru, jako je například velikost odsazení, na základě projektu. Další informace o podpoře sady Visual Studio pro soubory EditorConfig naleznete v [tématu Vytvoření nastavení přenosného editoru pomocí EditorConfig](../ide/create-portable-custom-editor-options.md).

Ve většině případů při implementaci služby jazyka Visual Studio není potřeba žádná další práce pro podporu univerzálních vlastností EditorConfig. Základní editor automaticky zjišťuje a čte soubor .editorconfig, když uživatelé otevírají soubory, a nastaví příslušnou textovou vyrovnávací paměť a možnosti zobrazení. Pro úpravy, jako jsou karty a mezery, se však některé jazykové služby rozhodnou použít vhodnou možnost kontextového zobrazení textu, nikoli globální nastavení. V těchto případech musí být jazyková služba aktualizována tak, aby podporovala soubory EditorConfig.

Následují změny, které jsou potřebné k aktualizaci jazykové služby pro podporu souborů EditorConfig nahrazením globální _možnosti specifické pro jazyk_ _kontextovou_ volbou:

## <a name="indent-style"></a>Styl odsazení

Možnosti specifické pro jazyk | Kontextové možnosti
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Velikost odsazení

Možnosti specifické pro jazyk | Kontextové možnosti
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Velikost tabulátoru

Možnosti specifické pro jazyk | Kontextové možnosti
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Viz také

- [Vytvoření nastavení přenosného editoru pomocí EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Rozšíření editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md)
