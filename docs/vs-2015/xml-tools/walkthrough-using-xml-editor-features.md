---
title: 'Návod: Používání funkcí editoru XML | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b054f7bfc4a70ee19e60315e3e7bc2a790db3cba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252281"
---
# <a name="walkthrough-using-xml-editor-features"></a>Návod: Používání funkcí editoru XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kroky v tomto názorném postupu ukazují, jak vytvořit nový dokument XML. Průvodce také používá některé funkce v editoru XML, které jí umožňují velmi cennou pomůckou pro vytváření XML.  
  
> [!NOTE]
>  Před zahájením návodu, uložte soubor hireDate.xsd (uvedené níže v tomto tématu) do místního počítače.  
  
### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Vytvořte nový soubor XML a přidružte jej k schématu XML  
  
1.  Na **souboru** nabídky, přejděte k **nový**a klikněte na tlačítko **souboru**.  
  
2.  Vyberte **soubor XML** v **šablony** podokně a klepněte na **otevřít**.  
  
     Nový soubor je otevřen v editoru. Tento soubor obsahuje deklaraci XML výchozí `<?xml version="1.0" encoding="utf-8">`.  
  
3.  V okně Vlastnosti dokumentu, klikněte na tlačítko Procházet (**...** ) na **schémata** pole.  
  
     **Schémata XSD** se zobrazí dialogové okno.  
  
4.  Klikněte na tlačítko **přidat**.  
  
     **Otevřít schéma XSD** se zobrazí dialogové okno.  
  
5.  Vyberte soubor hireDate.xsd a klikněte na tlačítko **otevřít**.  
  
6.  Klikněte na tlačítko **OK**.  
  
     Schéma XML je teď přidružený k dokumentu XML. Schématu XML se používá k ověření dokumentu. Také se používá technologii IntelliSense k naplnění seznamu členů platné prvky.  
  
### <a name="to-add-data"></a>Chcete-li přidat data  
  
1.  Typ `<` podokna editoru.  
  
     Seznam členů obsahuje položky, je to možné:  
  
    -   **! –** a přidejte komentář.  
  
    -   **! Typ dokumentu** přidat typ dokumentu.  
  
    -   **?** Chcete-li přidat instrukce pro zpracování.  
  
    -   **Zaměstnanec** přidat kořenový element.  
  
2.  Vyberte  **\<!--** přidat uzel komentáře a stiskněte klávesu ENTER.  
  
     Editor vloží koncová značka komentáře a umístí kurzor mezi počáteční a koncové značky pro komentáře.  
  
3.  Zadejte **soubor Test XML**.  
  
4.  Na nový řádek, zadejte `<`a vyberte **zaměstnance** ze seznamu členů.  
  
     Editor přidá na začátek elementu XML `<employee`. V tomto okamžiku můžete přidat atributy pro element nebo můžete zavřít počáteční značce zadáním `>`.  
  
5.  Typ `>` zavřete značky.  
  
6.  Editor přidá koncová značka. Koncová značka se přidá s podtržení vlnovkou udávající chybu ověřování. Popisek zobrazí zprávu: element 'zaměstnance' má neúplný obsah. Byl očekáván 'ID'.  
  
7.  Typ `<` a vyberte **ID** ze seznamu členů. Zadejte `>`.  
  
     Přidá XML element editor `<ID></ID>`a umístí kurzor po ID počáteční značka.  
  
8.  Typ **abc**.  
  
     **Abc** text obsahuje podtržení vlnovkou. Popisek zobrazí zprávu: element 'ID' má neplatnou hodnotu podle jeho datového typu.  
  
9. Klikněte pravým tlačítkem na ID elementu a vyberte **přejít k definici**.  
  
     Editor hireDate.xsd soubor se otevře v novém okně dokumentu a umístí kurzor na definici schématu element ID.  
  
10. Vraťte se do souboru XML a nahraďte **abc** text s **123**.  
  
     V části hodnotu elementu ID jsou vymazány podtržení vlnovkou a popisu. Popis pro koncovou značku zaměstnance nyní zobrazí zprávu: element 'zaměstnance' má neúplný obsah. Očekávané "přijetím datum".  
  
11. Umístěte kurzor po ID koncovou značku, zadejte v `<`, vyberte datum přijetí ze seznamu členů a poté zadejte `>`.  
  
     Přidá XML element editor `<hire-date></hire-date>`a umístí kurzor po datum přijetí počáteční značka.  
  
12. Zadejte **2003-01-10** pro hodnotu Datum přijetí.  
  
### <a name="to-format-the-xml-document"></a>Formát dokumentu XML  
  
1.  Vyberte **formátovat dokument** tlačítko na panelu nástrojů editoru XML.  
  
     Dokument XML je přeformátovali.  
  
### <a name="to-save-the-xml-document"></a>Uložení dokumentu XML  
  
1.  Z **souboru** nabídce vyberte možnost **uložit jako**.  
  
     **Uložit soubor jako** se zobrazí dialogové okno. Výchozí název je "XMLFile1".  
  
2.  Zadejte název souboru a umístění dokumentu XML a klikněte na tlačítko **Uložit**.  
  
## <a name="hiredatexsd-file"></a>hireDate.xsd souboru  
 Následující soubor schématu je používán návodu.  
  
```  
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také  
 [Editor XML](../xml-tools/xml-editor.md)

