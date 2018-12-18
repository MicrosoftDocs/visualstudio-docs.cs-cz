---
title: Funkce IntelliSense editoru XML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4dbb96ffcca47303a90b1ff4c71643a63f6b4aa5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830740"
---
# <a name="xml-editor-intellisense-features"></a>Funkce IntelliSense editoru XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Editor poskytuje úplné funkce IntelliSense srovnatelná s hodnotou jiné editory jazyk v sadě Visual Studio. Tato část vysvětluje, jak můžete pomocí technologie IntelliSense se schéma XML definice jazyk (XSD) a dokumentů XSLT.  
  
## <a name="intellisense-in-an-xsd-document"></a>Technologie IntelliSense v XSD dokumentu  
 Po schéma je spojen s vaším dokumentem, získáte rozevírací seznam očekávané prvky kdykoli zadáte `"<"` nebo klikněte na tlačítko **zobrazit seznam členů objektu** tlačítko na panelu nástrojů editoru XML. Informace o tom, jak přidružit schémat XML dokumentů najdete v tématu [ověření dokumentu XML](../xml-tools/xml-document-validation.md).  
  
 Když zadáte místo z uvnitř počáteční značku, budete mít také rozevírací seznam zobrazující všechny atributy, které mohou být přidány do aktuálního prvku.  
  
 Po zadání `"="` pro hodnotu atributu nebo úvodní uvozovka pro hodnotu, je také získat seznam možných hodnot pro tento atribut. Hodnoty jsou zobrazeny pouze, pokud schéma obsahuje výčtové hodnoty přes `xsd:enumeration` omezující vlastnosti, nebo pokud je atribut `Boolean` typu. Také poskytuje seznam kódů známých jazyků, technologie IntelliSense pro `xml:lang` ani na žádného `simpleType` , která je odvozena z `xsd:language`. Technologie IntelliSense seznam známých `targetNamespace` poskytuje hodnoty pro deklarace oboru názvů.  
  
 Když zadáte také poskytuje technologie IntelliSense seznam možných hodnot `">"` zavřete počáteční značku, pokud je element `simpleType`. Chování prvků se podobá chování pro atributy, které jsou popsané v předchozím odstavci.  
  
 Popisy tlačítek se zobrazí také na seznamy IntelliSense na základě `xsd:annotation` a `xsd:documentation` informace nalézt v přidružené schéma.  
  
## <a name="intellisense-in-an-xslt-document"></a>Technologie IntelliSense v dokumentu XSLT  
 Jakmile přidáte do dokumentu XSLT s názvem šablony nebo atribut, můžete vložit následující technologie IntelliSense:  
  
- Atribut nastavit názvy.  
  
- Režimy šablony.  
  
- Názvy šablon.  
  
- Názvy parametrů pro danou režimu.  
  
- Názvy parametrů pro danou uvedené šabloně.  
  
  Další informace najdete v tématu [návod: používání IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md) tématu.  
  
## <a name="auto-completion"></a>Automatické dokončování  
 XML editor také umožňuje úpravy XML jednodušší vyplněním požadované syntaxe XML pro vás. Například zadejte následující počáteční značku:  
  
 `<book>`  
  
 XML editor vyplní koncovou značku a umístí kurzor po počáteční značce. Následuje příklad ("&#124;" poznámky pozice kurzoru):  
  
 `<book>`&#124;`</book>`  
  
 Vzhledem k tomu, že hodnoty atributů musí mít vždy uvozovky, vyplní editoru jazyka XML v nabídkách za vás. Například zadejte následující příkaz:  
  
 `<book title=`  
  
 XML editor přidá uvozovky a umístí kurzor mezi uvozovky:  
  
 `<book title="`&#124;`"`  
  
 Obdobně editoru XML také následující syntaxi XML automaticky vloží za vás:  
  
- Konec instrukce pro zpracování:  `?>`  
  
- Konec bloku CDATA: `]]>`  
  
- Ukončit komentář: `-->`  
  
- Konec deklarace DTD: `>`  
  
  XML Editor má také možnost Vložit obor názvů deklarace, pokud vyberete element kvalifikovaný obor názvů nebo atribut z seznam technologie IntelliSense a obor názvů pro tento atribut nebo element není v oboru.  
  
  Například, pokud jste vybrali `e:Book` prvku ze seznamu technologie IntelliSense, kde předpona, která je vázán na `http://books` obor názvů, který nebyl deklarován v dokumentu XML editor vloží požadovaný obor názvů deklarace za vás. Výsledný text XML je následující:  
  
  `<e:Book xmlns:e="http://books"`  
  
## <a name="brace-matching"></a>Párování závorek  
 XML editor poskytuje zvýraznění získáte okamžitou zpětnou vazbu na prvek, který jste právě zavřeli závorek. Můžete také použít klávesovou zkratku (CTRL +]) přecházet z jednoho závorek k odpovídající závorce.  
  
 XML editor se to dělá pro následující položky:  
  
-   Odpovídající počáteční a koncovou značku.  
  
-   Nějaká dvojice "\<" nebo ">" ostrých závorek.  
  
-   Začátek a konec komentáře.  
  
-   Začátek a konec instrukce pro zpracování.  
  
-   Začátek a konec bloky CDATA.  
  
-   Začátek a konec deklarace DTD.  
  
-   Levé a pravé uvozovky u atributů.  
  
## <a name="modifying-the-intellisense-options"></a>Úprava možnosti technologie IntelliSense  
 Ve výchozím nastavení jsou povoleny funkce IntelliSense a automatické dokončování. Můžete to však změnit úpravou nastavení možnosti nástrojů.  
  
 **Automatické vložení** část **různé** ovládací prvky stránek následující chování:  
  
|Název|Popis|  
|----------|-----------------|  
|Zavřít značky|Vloží uzavírací značky pro nové prvky.|  
|Uvozovky atributu|Když zadáte nový název atributu, vloží uvozovky u hodnot atributů.|  
|Další kód|Dokončení komentáře, CDATA, DOCTYPE, pokyny pro zpracování a dalších deklarací značek.|  
  
#### <a name="to-change-the-auto-completion-behavior"></a>Chcete-li změnit chování automatického dokončování  
  
1.  Vyberte **možnosti** z **nástroje** nabídky.  
  
2.  Rozbalte **textový Editor**, rozbalte **XML**a vyberte **různé**.  
  
3.  Ujistěte se, všechny změny **automatické vkládání** části a klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také  
 [XML Editor](../xml-tools/xml-editor.md)   
 [Používání atributu IntelliSense](../ide/using-intellisense.md)   
 [Návod: Používání IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md)



