---
title: Ověřování dokumentu XML v editoru XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 389328e97f29d97962353e86f73c39c7c5459bfc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592409"
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
