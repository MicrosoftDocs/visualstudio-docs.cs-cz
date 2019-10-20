---
title: 'Postupy: vytvoření dokumentu XML na základě schématu XSD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e48c48d6711a1eb21157122d13790e22688855
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670951"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Postupy: vytvoření dokumentu XML na základě schématu XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkce **Generovat ukázková data XML** generuje ukázkový soubor XML na základě vašeho souboru schématu XML (XSD).

 Tuto možnost můžete použít pro následující scénáře:

- Pro pochopení použití různých konstrukcí ve schématu.

- Potvrďte, že je schéma zamýšleno k tomu, aby.

  Funkce **Generovat vzor XML** je k dispozici pouze pro globální prvky a vyžaduje platnou sadu schémat XML.

  Tato funkce obvykle generuje platné dokumenty XML. Pokud však schéma obsahuje jednu nebo více z následujících možností, příklad nemusí být platný:

- Omezení identity `xs:key`, `xs:keyref` a `xs:unique`.

- `xs:pattern` omezující vlastnosti.

- Výčty typu `xs:QName`.

- typy `xs:ENTITY`, `xs:ENTITIES` a `xs:NOTATION`.

  Všimněte si také, že `xs:base64Binary` obsah bude vygenerován pouze v případě, že ve schématu pro daný typ dojde k výčtům.

### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Vygenerování dokumentu instance XML na základě souboru XSD

1. Postupujte podle kroků v tématu [Postupy: vytvoření a úprava souboru schématu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. V [Průzkumníku schémat XML](../xml-tools/xml-schema-explorer.md)klikněte pravým tlačítkem na `PurchaseOrder` globální prvek. Vyberte **vytvořit ukázkový kód XML**.

     Když vyberete tuto možnost, vytvoří se soubor PurchaseOrder. XML s následujícím ukázkovým obsahem XML a otevře se v editoru XML:

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```

## <a name="see-also"></a>Viz také
 [Práce s daty XML](../xml-tools/working-with-xml-data.md)
