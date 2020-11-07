---
title: Ověřování dokumentu XML v editoru XML
description: Přečtěte si o ověřování dokumentů XML v editoru XML a o tom, jak kontroluje syntaxi XML 1,0 a provádí ověřování dat při psaní.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec38cb416f764990252b1e58c2322bea8be94d15
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351450"
---
# <a name="xml-document-validation"></a>Ověření dokumentu XML

Editor XML kontroluje syntaxi XML 1,0 a při psaní provádí také ověřování dat. Editor se může ověřit pomocí definice typu dokumentu (DTD) nebo schématu. Červené podtržení vlnovkou zvýrazní všechny chyby XML 1,0 ve správném formátu. Modře podtržení vlnovkou znázorňují sémantické chyby založené na ověřování DTD nebo schématu. Každá chyba má přidruženou položku v seznamu chyb. Chybovou zprávu můžete zobrazit také pozastavením myši na podtržení vlnovkou.

Schémata použitá při ověřování se nacházejí v porovnání s `targetNamespace` deklarací zkompilovaného schématu v rámci deklarace xmlns elementu. Kompilovaná schémata jsou načítána z jednoho z následujících umístění, která jsou uvedena v pořadí podle priority:

- Z názvu souboru zadaného v poli **schémata** okna **vlastností** dokumentu.

- Vložené schéma nebo DTD.

- Externí deklarace DTD nebo `xsd:schemaLocation` atribut a `xsd:noNamespaceSchemaLocation`

- Identifikátor URI oboru názvů schématu XDR schématu "x-Schema".

Schémata lze také najít v následujících dalších umístěních, pokud má schéma neprázdný cílový obor názvů:

- Další okno editoru, které obsahuje schéma.

- Schéma v aktuálním řešení.

- Schéma z adresáře mezipaměti schématu.

## <a name="xslt-files"></a>Soubory XSLT
Při úpravách souboru XSLT se k ověřování používá soubor *XSLT. xsd* umístěný v mezipaměti schématu. Chyby ověřování se zobrazují modře podtržení vlnovkou. Chyby z kompilátoru XSLT se zobrazí jako červené vlnovky.

## <a name="xml-schema-xsd-files"></a>Soubory schématu XML (XSD)
Při úpravách souboru schématu XML se k ověřování používá soubor *xsdschema. xsd* umístěný v mezipaměti schématu. Chyby ověřování se zobrazují modře podtržení vlnovkou. Všechny chyby při kompilaci jsou také zobrazeny červeně vlnovkou vlnovkou.

## <a name="see-also"></a>Viz také

- [Editor XML](../xml-tools/xml-editor.md)
