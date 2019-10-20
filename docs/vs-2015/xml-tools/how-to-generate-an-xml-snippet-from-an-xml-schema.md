---
title: 'Postupy: generování fragmentu XML ze schématu XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e3d90185180cac5f526594650bde0a8f380c7668
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666526"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Postupy: generování fragmentu XML ze schématu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML má možnost generovat fragmenty XML ze schématu XML schématu definice jazyka (XSD). Například při vytváření souboru XML, který je umístěn vedle názvu elementu, lze stisknutím klávesy TAB naplnit element daty XML generovanými z informací o schématu pro daný element.

 Tato funkce je k dispozici pouze u elementů. Platí taky následující pravidla:

- Element musí mít přidružený typ schématu. To znamená, že element musí být platný vzhledem k některému přidruženému schématu. Typ schématu nemůže být abstraktní a typ musí obsahovat požadované atributy nebo požadované podřízené prvky.

- Aktuální prvek v editoru musí být prázdný bez atributů. Následující jsou například všechny platné

  - `<Account`

  - `<Account>`

  - `<Account></Account>`

- Kurzor musí být umístěn hned napravo od názvu elementu.

  Vygenerovaný fragment obsahuje všechny požadované atributy a prvky. Pokud je `minOccurs` větší než jedna, požadovaný minimální počet instancí tohoto prvku je zahrnut ve fragmentu až do maximálního počtu instancí 100. Všechny pevné hodnoty nalezené ve schématu mají za následek pevné hodnoty fragmentu. prvky `xsd:any` a `xsd:anyAttribute` jsou ignorovány a mají za následek žádné další konstrukce fragmentu kódu.

  Výchozí hodnoty jsou vygenerovány a označeny jako upravitelné hodnoty. Pokud schéma určuje výchozí hodnotu, použije se tato výchozí hodnota. Pokud je však výchozí hodnota schématu prázdný řetězec, Editor vygeneruje výchozí hodnoty následujícím způsobem:

- Pokud typ schématu obsahuje všechny omezující vlastnosti výčtu, a to buď přímo, nebo nepřímo prostřednictvím kteréhokoli člena typu sjednocení, jako výchozí se použije první Výčtová hodnota nalezená v objektovém modelu schématu.

- Pokud je typ schématu typ Atomic, Editor získá typ atomie a vloží název atomické typu. Pro odvozený jednoduchý typ používá základní jednoduchý typ. Jako typ seznamu je `itemType` typ atomická. Pro sjednocení je typ atomický typ prvního `memberType`.

## <a name="example"></a>Příklad
 Postup v této části ukazuje, jak používat funkci fragmentu kódu XML, který je vygenerovaný schématem editoru XML.

> [!NOTE]
> Než začnete s tímto postupem, uložte soubor schématu do místního počítače.

#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Vytvoření nového souboru XML a jeho přidružení ke schématu XML

1. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na možnost **soubor**.

2. V podokně **šablony** vyberte **soubor XML** a klikněte na **otevřít**.

     V editoru se otevře nový soubor. Soubor obsahuje výchozí deklaraci XML `<?xml version="1.0" encoding="utf-8">`.

3. V okně Vlastnosti dokumentu klikněte na tlačítko pro procházení ( **...** ) v poli **schémata** .

     Zobrazí se dialogové okno **schémata XSD** .

4. Klikněte na tlačítko **Přidat**.

     Zobrazí se dialogové okno **otevřít schéma XSD** .

5. Vyberte soubor schématu a klikněte na **otevřít**.

6. Klikněte na tlačítko **OK**.

     Schéma XML je nyní přidruženo k dokumentu XML.

#### <a name="to-generate-an-xml-snippet"></a>Generování fragmentu XML

1. Zadejte `<` v podokně editoru.

2. Seznam členů zobrazuje možné položky:

     Přidejte komentář **!--** .

     **! DOCTYPE** pro přidání typu dokumentu

     **?** Přidání instrukce pro zpracování.

     **Kontaktujte** pro přidání kořenového prvku.

3. Vyberte ze seznamu členů položku **kontakt** a stiskněte klávesu ENTER.

     Editor přidá počáteční značku `<Contact` a umístí kurzor za název elementu.

4. Stisknutím klávesy TAB vygenerujte data XML prvku `Contact` na základě jeho informací o schématu.

### <a name="input"></a>Vstup
 Následující soubor schématu se používá v tomto návodu.

```
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>Výstup
 Následuje data XML, která jsou generována v závislosti na informacích schématu přidružených k prvku `Contact`. Položky označené jako `bold` určují upravitelná pole ve fragmentu kódu XML.

```
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>Viz také
 [Fragmenty kódu XML](../xml-tools/xml-snippets.md) [Postupy: použití fragmentů kódu XML](../xml-tools/how-to-use-xml-snippets.md)
