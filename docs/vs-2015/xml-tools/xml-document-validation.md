---
title: Ověření dokumentu XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee5d3cff260346a5bcc1806b09b955642c608f14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669495"
---
# <a name="xml-document-validation"></a>Ověření dokumentu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML kontroluje syntaxi XML 1,0 a při psaní provádí také ověřování dat. Editor se může ověřit pomocí definice typu dokumentu (DTD) nebo schématu. Červené podtržení vlnovkou zvýrazní všechny chyby XML 1,0 ve správném formátu. Modře podtržení vlnovkou znázorňují sémantické chyby založené na ověřování DTD nebo schématu. Každá chyba má přidruženou položku v seznamu chyb. Chybovou zprávu můžete zobrazit také pozastavením myši na podtržení vlnovkou.

 Schémata použitá při ověřování jsou nalezena tak, že odpovídají `targetNamespace` zkompilovaného schématu s deklarací xmlns elementu. Kompilovaná schémata jsou načítána z jednoho z následujících umístění, která jsou uvedena v pořadí podle priority:

- Z názvu souboru zadaného v dokumentu okno Vlastnosti v poli **schémata** .

- Vložené schéma nebo DTD.

- Externí deklarace DTD nebo atribut `xsd:schemaLocation` a `xsd:noNamespaceSchemaLocation`

- Identifikátor URI oboru názvů schématu XDR schématu "x-Schema".

  Schémata lze také najít v následujících dalších umístěních, pokud má schéma neprázdný cílový obor názvů:

- Další okno editoru, které obsahuje schéma.

- Schéma v aktuálním řešení.

- Schéma z adresáře mezipaměti schématu.

## <a name="xslt-files"></a>Soubory XSLT
 Při úpravách souboru XSLT se k ověřování používá soubor XSLT. xsd umístěný v mezipaměti schématu. Chyby ověřování se zobrazují modře podtržení vlnovkou. Chyby z kompilátoru XSLT se zobrazí jako červené vlnovky.

## <a name="xml-schema-xsd-files"></a>Soubory schématu XML (XSD)
 Při úpravách souboru schématu XML se k ověřování používá soubor xsdschema. xsd umístěný v mezipaměti schématu. Chyby ověřování se zobrazují modře podtržení vlnovkou. Všechny chyby při kompilaci jsou také zobrazeny červeně vlnovkou vlnovkou.

## <a name="see-also"></a>Viz také
 [Editor XML](../xml-tools/xml-editor.md)
