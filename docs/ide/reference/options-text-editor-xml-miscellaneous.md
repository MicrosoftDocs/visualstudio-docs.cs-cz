---
title: Možnosti, textový Editor, XML, různé
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c6def0a2e374e5297d25d17f4ea4a4a113d4bd56
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673497"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Možnosti, textový Editor, XML, různé
Použití **různé** stránky vlastností, chcete-li změnit nastavení automatického doplňování spolu se schématem pro Editor XML. Chcete-li otevřít **možnosti** dialogovém okně klikněte na tlačítko **nástroje** nabídky a pak klikněte na tlačítko **možnosti**. Pro přístup **různé** vlastnost stránce, rozbalte **textový Editor** > **XML** > **různé**uzlu.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="auto-insert"></a>Automatické vkládání  
**Zavřít značky**  
Textový Editor přidá zavřít značky při vytváření elementů XML. Pokud je vybrána počáteční značky elementu, editor vloží odpovídající uzavírací značka, včetně odpovídající Předpona oboru názvů. Toto zaškrtávací políčko je ve výchozím nastavení zaškrtnuto.  
  
**Uvozovky atributu**  
Při vytváření atributy ve formátu XML, editor vloží `="` a `"` znaků a pozice blikajícího kurzoru (**^**) v uvozovkách. Toto zaškrtávací políčko je ve výchozím nastavení zaškrtnuto.  
  
**Deklarace Namespace**  
Editor automaticky vloží deklarace oboru názvů, bez ohledu na to se v případě potřeby zapíná. Toto zaškrtávací políčko je ve výchozím nastavení zaškrtnuto.  
  
**Jiné značky (komentáře, CDATA)**  
Komentáře, CDATA, DOCTYPE, pokyny pro zpracování a jiný kód je autocompleted. Toto zaškrtávací políčko je ve výchozím nastavení zaškrtnuto.  
  
## <a name="network"></a>Sítě  
**Automaticky stahovat specifikace DTD a schémata**  
Schémata a definice typu dokumentu (DTD) se automaticky stáhnou z umístění protokolu HTTP. Tato funkce používá System.Net s detekcí autoproxy serveru povolené. Toto zaškrtávací políčko je ve výchozím nastavení zaškrtnuto.  
  
## <a name="outlining"></a>Sbalování  
**Po otevření souborů vstoupit do režimu sbalování**  
Při otevření souboru se změní na funkci sbalování. Toto zaškrtávací políčko je ve výchozím nastavení zaškrtnuto.  
  
## <a name="caching"></a>Ukládání do mezipaměti  
**Schémata**  
Určuje umístění mezipaměti schémat. Tlačítko Procházet (...) aktuální umístění mezipaměti schémat se otevře v novém okně. Výchozí umístění je  *\<Management Studio instalační_adresář >* \Xml\Schemas.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: vytvoření dokumentace XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Generování kódu](../code-generation-in-visual-studio.md)