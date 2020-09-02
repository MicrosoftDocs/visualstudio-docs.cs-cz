---
title: Rozšiřování jazykové služby na podporu EditorConfig
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699588"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Podpora EditorConfig pro vaši jazykovou službu

Soubory [EditorConfig](https://editorconfig.org/) umožňují popsat možnosti běžných textových editorů, jako je například velikost odsazení, na základě jednotlivých projektů. Další informace o podpoře sady Visual Studio pro soubory EditorConfig najdete v tématu [Vytvoření nastavení přenosného editoru pomocí EditorConfig](../ide/create-portable-custom-editor-options.md).

Ve většině případů při implementaci jazykové služby sady Visual Studio není potřeba žádná další práce, která by podporovala univerzální vlastnosti EditorConfig. Základní editor automaticky zjistí a přečte soubor. editorconfig, když uživatel otevře soubory a nastaví odpovídající vyrovnávací paměť textu a možnosti zobrazení. U úprav, jako jsou tabulátory a mezery, se ale některé jazykové služby místo použití globálních nastavení použijí jako vhodná možnost zobrazení kontextového textu. V těchto případech je potřeba aktualizovat jazykovou službu tak, aby podporovala soubory EditorConfig.

Níže jsou uvedené změny, které jsou potřeba k aktualizaci jazykové služby na podporu souborů EditorConfig, nahrazením globální možnosti _specifické pro konkrétní jazyk_ pomocí _kontextové_ možnosti:

## <a name="indent-style"></a>Styl odsazení

Možnosti specifické pro jazyk | Kontextové možnosti
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. fInsertTabs<br/>Microsoft. VisualStudio. Package. LanguagePreferences. InsertTabs|! textBufferOptions. getoptionvalue (DefaultOptions. ConvertTabsToSpacesOptionId)<br/>! textView. Options. getoptionvalue (DefaultOptions. ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Zvětšit velikost

Možnosti specifické pro jazyk | Kontextové možnosti
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. uIndentSize<br/>Microsoft. VisualStudio. Package. LanguagePreferences. InsertTabs. IndentSize|textBufferOptions. getoptionvalue (DefaultOptions. IndentSizeOptionId)<br/>textView. Options. getoptionvalue (DefaultOptions. IndentSizeOptionId)

## <a name="tab-size"></a>Velikost tabulátoru

Možnosti specifické pro jazyk | Kontextové možnosti
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. uTabSize<br/>Microsoft. VisualStudio. Package. LanguagePreferences. InsertTabs. TabSize|textBufferOptions. getoptionvalue (DefaultOptions. TabSizeOptionId)<br/>textView. Options. getoptionvalue (DefaultOptions. TabSizeOptionId)

## <a name="see-also"></a>Viz také

- [Vytvoření nastavení přenosného editoru pomocí EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Rozšíření editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md)
