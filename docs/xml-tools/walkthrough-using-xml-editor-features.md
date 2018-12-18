---
title: 'Návod: Používání funkcí editoru XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afda2968ece2a18b7abdc2c4c35e4353206cbe42
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693822"
---
# <a name="walkthrough-use-xml-editor-features"></a>Návod: Použití funkcí editor XML

Kroky v tomto návodu ukazují, jak vytvořit nový dokument XML. Průvodce také používá některé z funkcí editoru XML, které umožňují cenné XML pro vytváření obsahu.

> [!NOTE]
> Před spuštěním průvodce, uložte *hireDate.xsd* souboru (uvedené níže v tomto tématu) do místního počítače.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>K vytvoření nového souboru XML a přidružte ji k schématu XML

1.  Na **soubor** nabídky, přejděte na příkaz **nový**a klikněte na tlačítko **soubor**.

2.  Vyberte **souboru XML** v **šablony** panelu a klikněte na tlačítko **otevřete**.

     Nový soubor se otevře v editoru. Tento soubor obsahuje deklaraci XML výchozí `<?xml version="1.0" encoding="utf-8">`.

3.  V okně vlastností dokumentu klikněte na tlačítko Procházet (**...** ) na **schémata** pole.

     **XSD schémata** se zobrazí dialogové okno.

4.  Klikněte na tlačítko **přidat**.

     **Otevřete schématu XSD** se zobrazí dialogové okno.

5.  Vyberte *hireDate.xsd* souboru a klikněte na tlačítko **otevřete**.

6.  Click **OK**.

     Schéma XML je nyní přidružené k dokumentu XML. Schéma XML slouží k ověření dokumentu. Také se používá technologii IntelliSense k naplnění seznamu členů platný elementů.

## <a name="to-add-data"></a>Chcete-li přidat data

1.  Typ `<` v podokně editor.

     Zobrazí se seznam členů možné položky:

    -   **!--** přidání komentáře.

    -   **! DOCTYPE** přidejte typ dokumentu.

    -   **?** Chcete-li přidat instrukce pro zpracování.

    -   **Zaměstnanec** přidat kořenový element.

2.  Vyberte **<!--** přidat uzel komentáře a stiskněte klávesu **Enter**.

     Editor vloží koncová značka komentáře a umístí kurzoru mezi počáteční a koncové značky pro komentáře.

3.  Zadejte **souboru XML testovací**.

4.  Na nový řádek, zadejte `<`a vyberte **zaměstnanec** ze seznamu členů.

     Editor přidá začátku elementu XML, `<employee`. V tomto okamžiku můžete přidat atributy do elementu nebo můžete zavřít počáteční značce zadáním `>`.

5.  Typ `>` zavřete značky.

6.  Editor přidá koncová značka. Koncová značka se přidá s vlnovkou indikující chybu ověření. **Popisek** zobrazí zprávu: **má element "zaměstnanec" nekompletní obsah. Očekávaný 'ID'**.

7.  Typ `<` a vyberte **ID** ze seznamu členů. Pak zadejte `>`.

     Přidá XML element editor `<ID></ID>`a umístí kurzor po ID počáteční značka.

8.  Typ **abc**.

     **Abc** text má vlnovkou. **Popisek** zobrazí zprávu: **element "ID" má neplatnou hodnotu podle jeho datového typu**.

9. Klikněte pravým tlačítkem na ID elementu a vyberte **přejít k definici**.

     Otevře se editor *hireDate.xsd* soubor v novém okně dokumentu a umístí kurzor na definici ID schématu elementu.

10. Vraťte se do souboru XML a nahraďte **abc** textu s **123**.

     Podtržení vlnovkou a **popisek** vyjmuty pod hodnota ID elementu. **Popisek** pro zaměstnance koncové značky nyní zobrazí zprávu: **má element "zaměstnanec" nekompletní obsah. Očekávání, datum přijetí'**.

11. Umístěte kurzor za koncovou značku ID, zadejte v `<`, vyberte **datum přijetí** ze seznamu členů a poté zadejte `>`.

     Přidá XML element editor `<hire-date></hire-date>`a umístí kurzor po datum přijetí počáteční značka.

12. Zadejte **2003-01-10** pro hodnotu Datum přijetí.

## <a name="to-format-the-xml-document"></a>K formátování v dokumentu XML

- Vyberte **formátovat dokument** tlačítka panelu nástrojů editoru XML.

    V dokumentu XML je naformátována.

## <a name="to-save-the-xml-document"></a>Uložení dokumentu XML

1.  Z **soubor** nabídce vyberte možnost **uložit jako**.

     **Uložit soubor jako** se zobrazí dialogové okno. Výchozí název souboru je *'XMLFile1'*.

2.  Zadejte název souboru a umístění v dokumentu XML a klikněte na tlačítko **Uložit**.

## <a name="hiredatexsd-file"></a>soubor hireDate.xsd
 Následující schéma soubor je používán návodu.

```xml
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

## <a name="see-also"></a>Viz také:

- [Editor XML](../xml-tools/xml-editor.md)