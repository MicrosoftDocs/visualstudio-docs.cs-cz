---
title: 'Postupy: Vytvoření dokumentu XML na základě schématu XSD'
description: Naučte se používat funkci generovat ukázkovou XML k vytvoření dokumentu XML na základě schématu XSD.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bc802d48bc76bc5f0c6a4c272bf994e87bb8443
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970306"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Postupy: vytvoření dokumentu XML na základě schématu XSD

Funkce **Generovat ukázková data XML** generuje ukázkový soubor XML na základě vašeho souboru schématu XML (XSD).

Tuto možnost můžete použít pro následující scénáře:

- Pro pochopení použití různých konstrukcí ve schématu.

- Potvrďte, že je schéma zamýšleno k tomu, aby.

Funkce **Generovat vzor XML** je k dispozici pouze pro globální prvky a vyžaduje platnou sadu schémat XML.

Tato funkce obvykle generuje platné dokumenty XML. Pokud však schéma obsahuje jednu nebo více z následujících možností, příklad nemusí být platný:

- `xs:key` `xs:keyref` Omezení identity, a `xs:unique` .

- `xs:pattern` omezující vlastnosti.

- Výčty `xs:QName` typu.

- `xs:ENTITY``xs:ENTITIES`typy, a `xs:NOTATION` .

Také si všimněte, že `xs:base64Binary` obsah bude vygenerován pouze v případě, že ve schématu pro daný typ dojde k výčtům.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Vygenerování dokumentu instance XML na základě souboru XSD

1. Postupujte podle kroků v tématu [Postupy: vytvoření a úprava souboru schématu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. V [Průzkumníku schémat XML](../xml-tools/xml-schema-explorer.md)klikněte pravým tlačítkem myši na `PurchaseOrder` globální prvek a vyberte možnost **Generovat ukázkový kód XML**.

     Když vyberete tuto možnost, PurchaseOrder. soubor *XML* s následujícím ukázkovým obsahem XML bude vygenerován a otevřen v editoru XML:

    ```xml
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
