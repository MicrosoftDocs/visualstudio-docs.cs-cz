---
title: Moduly plug-in správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699895"
---
# <a name="source-control-plug-ins"></a>Moduly plug-in správy zdrojového kódu
Referenční část modulu Plug-in Source Control Plug-in Obsahuje úplnou specifikaci rozhraní, která umožňuje integraci systémů správy zdrojového kódu s [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Určuje syntaxi a sémantiku různých funkcí a datových typů, které musí modul [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plug-in správy zdrojového kódu implementovat do rozhraní s integrovaným vývojovým prostředím (IDE).

## <a name="in-this-section"></a>V tomto oddílu
- [Funkce rozhraní API pro sčást dat](../extensibility/source-control-plug-in-api-functions.md) Uvádí funkce, které musí být implementovány modulu plug-in správy zdrojového kódu, aby bylo možné splnit rozhraní api modulu plug-in správy zdrojového kódu.

- [Funkce zpětného volání implementované ide](../extensibility/callback-functions-implemented-by-the-ide.md) Popisuje funkce, které modul plug-in správy zdrojového kódu používá k předání informací zpět do ide při provádění určitých příkazů.

- [Čítače výčtu](../extensibility/enumerators.md) Zobrazí seznam datových typů čítače v rozhraní API modulu plug-in správy zdrojového kódu, o kterém musí modul plug-in správy zdrojového kódu vědět.

- [Příznaky schopností](../extensibility/capability-flags.md) Popisuje `SCC_CAP_xxx` příznaky, které označují možnosti zprostředkovatele.

- [Bitové příznaky používané určitými příkazy](../extensibility/bitflags-used-by-specific-commands.md) Uvádí příznaky, které jsou užitečné v kontextu konkrétní příkazy.

- [Kódy chyb](../extensibility/error-codes.md) Uvádí běžné chybové hodnoty `SCCTRN`vrácené funkcemi jako .

- [Řetězce používané jako klíče pro vyhledání modulu plug-in správy zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Popisuje klíče pro přístup k registru najít modul plug-in správy zdrojového kódu.

- [MSSCCPRJ. SCC File](../extensibility/mssccprj-scc-file.md) Popisuje soubor na straně klienta, který obsahuje informace neprůhledné ide, ale který je používán modul plug-in správy zdrojového kódu k vyhledání řešení nebo projektu v řízení verzí.

- [Doporučené postupy pro implementaci modulu plug-in správy zdrojového kódu](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Poskytuje kolekci důležitých technických připomenutí, která si můžete pamatovat při implementaci rozhraní PLUG-in source control.

- [Omezení délky řetězců](../extensibility/restrictions-on-string-lengths.md) Popisuje omezení v rozhraní API modulu plug-in správy zdrojového kódu na délky řetězců používaných v různých funkcích.

- [Slovníček pojmů](../extensibility/source-control-plug-in-glossary.md) Obsahuje užitečné termíny a jejich definice pro čtení dokumentace sady Plug-in správy zdrojového kódu.

- [Postup: Vypnutí upozornění na kompatibilitu modulů plug-in správy zdrojového kódu](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Popisuje, jak zakázat upozornění.

## <a name="related-sections"></a>Související oddíly
- [Ukázka modulu plug-in správy zdrojového kódu](https://www.microsoft.com/download/details.aspx?id=55984) Obsahuje ukázku funkcí modulu plug-in správy zdrojového kódu.

- [Průvodce testováním modulů plug-in správy zdrojového kódu](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Popisuje testovací postupy související s modulem plug-in správy zdrojového kódu.

- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md) Popisuje, jak vytvořit modul plug-in správy zdrojového kódu, který [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poskytuje funkce správy zdrojového kódu při použití uživatelského rozhraní správy zdrojového kódu(UI).

- [Referenční příručka sady Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md) Zobrazí seznam referenčních témat.
