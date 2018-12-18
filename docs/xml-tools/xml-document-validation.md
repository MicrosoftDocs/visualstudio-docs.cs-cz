---
title: Ověření dokumentu XML v editoru XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04b2e821abbbc7a24ce5b77b7374de617852cf2a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693835"
---
# <a name="xml-document-validation"></a>Ověření dokumentu XML

Editor souborů XML kontroluje syntaxe XML 1.0 a také provádí ověřování dat během psaní. Editor můžete ověřit pomocí definice typu dokumentu (DTD) nebo schéma. Červené podtržení vlnovkou zvýrazněte všechny chyby ve správném formátu XML 1.0. Modré podtržení vlnovkami Zobrazit sémantické chyby podle ověření DTD nebo schéma. Jednotlivé chyby má související záznam v seznamu chyb. Můžete také zobrazit chybová zpráva ponecháte myši nad vlnovkou.

 Nebyly nalezeny schémata použít ověřování pomocí odpovídajících `targetNamespace` kompilované schématu s xmlns deklaraci elementu. Kompilované schémata jsou načteny z jednoho z následujících umístění, uvedené v pořadí podle priority:

-   Z názvu souboru, který je zadaný v **schémata** pole dokumentu **vlastnosti** okno.

-   Vložené schéma nebo souboru DTD protokolu.

-   Externí DTD nebo `xsd:schemaLocation` a `xsd:noNamespaceSchemaLocation` atribut

-   "X-schema" XDR názvů schématu identifikátoru URI.

Schémata možné také najít v následujících umístěních další schéma má prázdný cílový obor názvů:

-   Další okno editor, který obsahuje schéma.

-   Schéma v aktuálním řešení.

-   Schéma z adresáře mezipaměti schématu.

## <a name="xslt-files"></a>Soubory XSLT
 Při úpravě soubor XSLT *xslt.xsd* soubor nachází v mezipaměti schématu se používá pro ověření. Jako modré podtržení vlnovkami zobrazí chyby ověření. Chyby z kompilátoru XSLT se zobrazí jako červené podtržení vlnovkou.

## <a name="xml-schema-xsd-files"></a>Soubory XML schématu (XSD)
 Při úpravě souboru schématu XML *xsdschema.xsd* soubor nachází v mezipaměti schématu se používá pro ověření. Jako modré podtržení vlnovkami zobrazí chyby ověření. Red vlnovkou jsou také uvedené chyby kompilace.

## <a name="see-also"></a>Viz také:

- [Editor XML](../xml-tools/xml-editor.md)