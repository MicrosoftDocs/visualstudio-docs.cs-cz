---
title: 'Návod: použití funkcí editoru XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ce7997e1002ced50dc4d8203d522feb0a6bbb49
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604451"
---
# <a name="walkthrough-use-xml-editor-features"></a>Návod: použití funkcí editoru XML

Kroky v tomto návodu ukazují, jak vytvořit nový dokument XML. Návod také používá některé z funkcí editoru XML, které usnadňují tvorbu XML.

> [!NOTE]
> Před zahájením tohoto návodu uložte soubor *HireDate. xsd* (v tomto tématu, který je uveden dále v tomto tématu) do místního počítače.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Vytvoření nového souboru XML a jeho přidružení ke schématu XML

1. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na možnost **soubor**.

2. V podokně **šablony** vyberte **soubor XML** a klikněte na **otevřít**.

     V editoru se otevře nový soubor. Soubor obsahuje výchozí deklaraci XML `<?xml version="1.0" encoding="utf-8">`.

3. V okně Vlastnosti dokumentu klikněte na tlačítko pro procházení ( **...** ) v poli **schémata** .

     Zobrazí se dialogové okno **schémata XSD** .

4. Klikněte na tlačítko **Přidat**.

     Zobrazí se dialogové okno **otevřít schéma XSD** .

5. Vyberte soubor *HireDate. xsd* a klikněte na tlačítko **otevřít**.

6. Klikněte na tlačítko **OK**.

     Schéma XML je nyní přidruženo k dokumentu XML. Schéma XML se používá k ověření dokumentu. Je také používána technologií IntelliSense k naplnění seznamu členů platných prvků.

## <a name="to-add-data"></a>Přidání dat

1. Zadejte `<` v podokně editoru.

     Seznam členů zobrazuje možné položky:

    - Přidejte komentář **!--** .

    - **! DOCTYPE** pro přidání typu dokumentu

    - **?** Přidání instrukce pro zpracování.

    - **Zaměstnanec** pro přidání kořenového prvku.

2. Vyberte **&lt;!--** a přidejte tak uzel komentáře a stiskněte klávesu **ENTER**.

     Editor vloží koncovou značku komentáře a umístí kurzor mezi značky začátek a konec komentáře.

3. Zadejte **soubor XML testu**.

4. Na novém řádku zadejte `<` a v seznamu členů vyberte **Zaměstnanec** .

     Editor přidá začátek XML elementu `<employee`. V tomto okamžiku můžete přidat atributy k elementu nebo můžete zavřít počáteční značku zadáním `>`.

5. Zadejte `>` pro zavření značky.

6. Editor přidá koncovou značku. Koncová značka se přidá s podtržením vlnovkou značící chybu ověřování. **Popisek** zobrazí zprávu: **v elementu ' Employee ' má neúplný obsah. Očekávalo se ID**.

7. Zadejte `<` a v seznamu členů vyberte **ID** . Pak zadejte `>`.

     Editor přidá XML element, `<ID></ID>` a umístí kurzor za počáteční značku ID.

8. Zadejte **ABC**.

     Text **ABC** má podtržení vlnovkou. **Popisek** zobrazí zprávu: **element ID má neplatnou hodnotu vzhledem k jeho datovému typu**.

9. Klikněte pravým tlačítkem na element ID a vyberte **Přejít k definici**.

     Editor otevře soubor *HireDate. xsd* v novém okně dokumentu a umístí kurzor na definici elementu schématu ID.

10. Vraťte se do souboru XML a nahraďte text **ABC** textem **123**.

     Podtržení vlnovkou a **popisy tlačítek** se v hodnotě elementu ID vymažou. **Popisek** pro koncovou značku zaměstnance teď zobrazí zprávu: **k elementu ' Employee ' má neúplný obsah. Bylo očekáváno Datum zařazení**.

11. Umístěte kurzor za značku konce ID, zadejte `<`, vyberte položku **Datum přijetí** ze seznamu členů a potom zadejte `>`.

     Editor přidá XML element, `<hire-date></hire-date>` a umístí kurzor po počáteční značku data nástupu.

12. Jako hodnotu data přijetí zadejte **2003-01-10** .

## <a name="to-format-the-xml-document"></a>Formátování dokumentu XML

- Na panelu nástrojů editoru XML vyberte tlačítko **formátovat dokument** nebo stiskněte klávesy **CTRL** +**E**,**D**.

   ![Tlačítko formátování dokumentu XML v aplikaci Visual Studio](media/format-xml-document.png)

   Dokument XML je přeformátován.

## <a name="to-save-the-xml-document"></a>Uložení dokumentu XML

1. V nabídce **soubor** vyberte **Uložit jako**.

     Zobrazí se dialogové okno **Uložit soubor jako** . Výchozí název souboru je *"XMLFile1"* .

2. Zadejte název souboru a umístění dokumentu XML a klikněte na **Uložit**.

## <a name="hiredatexsd-file"></a>ZaměstnánOd. xsd – soubor

V tomto návodu se používá následující soubor schématu:

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