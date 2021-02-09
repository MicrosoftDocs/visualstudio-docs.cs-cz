---
title: Moduly plug-in správy zdrojového kódu | Microsoft Docs
description: Články v této části popisují kompletní specifikaci rozhraní, která umožňuje integrovat systémy správy zdrojového kódu do sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab076cef7aaab96779e303ee7b85c8047eb6b52e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848114"
---
# <a name="source-control-plug-ins"></a>Moduly plug-in správy zdrojového kódu
Referenční část sady SDK modulu plug-in správy zdrojových kódů obsahuje kompletní specifikaci rozhraní, která umožňuje integraci systémů správy zdrojového kódu do nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Určuje syntaxi a sémantiku různých funkcí a datových typů, které musí modul plug-in správy zdrojových kódů implementovat pro rozhraní s [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaným vývojovým prostředím (IDE).

## <a name="in-this-section"></a>V tomto oddílu
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md) Obsahuje seznam funkcí, které musí být implementovány modulem plug-in správy zdrojových kódů, aby bylo možné dodržovat rozhraní API modulu plug-in správy zdrojového kódu.

- [Funkce zpětného volání implementované rozhraním IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Popisuje funkce, které modul plug-in správy zdrojových kódů používá k předání informací zpět do integrovaného vývojového prostředí při spuštění určitých příkazů.

- [Enumerátory](../extensibility/enumerators.md) Obsahuje seznam typů dat enumerátorů v rozhraní API modulu plug-in správy zdrojových kódů, o kterých musí modul plug-in správy zdrojových kódů doznat.

- [Příznaky schopností](../extensibility/capability-flags.md) Popisuje `SCC_CAP_xxx` příznaky, které označují schopnosti poskytovatele.

- [Bitflags používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md) Zobrazí seznam příznaků, které jsou užitečné v kontextu konkrétních příkazů.

- [Kódy chyb](../extensibility/error-codes.md) Zobrazuje běžné chybové hodnoty vrácené funkcemi jako `SCCTRN` .

- [Řetězce používané jako klíče pro vyhledání modulu plug-in správy zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Popisuje klíče pro přístup k registru, aby bylo možné najít modul plug-in správy zdrojového kódu.

- [MSSCCPRJ. Soubor SCC](../extensibility/mssccprj-scc-file.md) popisuje soubor na straně klienta, který obsahuje informace neprůhledné do rozhraní IDE, které používá modul plug-in správy zdrojových kódů k vyhledání řešení nebo projektu ve správě verzí.

- [Osvědčené postupy pro implementaci modulu plug-in správy zdrojových kódů](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Poskytuje kolekci důležitých technických připomenutí k zapamatování při implementaci rozhraní API modulu plug-in správy zdrojového kódu.

- [Omezení délky řetězců](../extensibility/restrictions-on-string-lengths.md) Popisuje omezení v rozhraní API modulu plug-in správy zdrojového kódu pro délky řetězců používané v různých funkcích.

- [Glosář](../extensibility/source-control-plug-in-glossary.md) Poskytuje užitečné výrazy a jejich definice pro čtení dokumentace k sadě SDK modulu plug-in správy zdrojového kódu.

- [Postupy: vypnutí upozornění kompatibility pro moduly plug-in správy zdrojového kódu](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Popisuje, jak zakázat upozornění.

## <a name="related-sections"></a>Související oddíly
- [Ukázka modulu plug-in správy zdrojového kódu](https://www.microsoft.com/download/details.aspx?id=55984) Poskytuje ukázku funkcí modulu plug-in správy zdrojového kódu.

- [Průvodce testováním pro moduly plug-in pro správu zdrojového kódu](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Popisuje postupy testování související s modulem plug-in správy zdrojových kódů.

- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md) Popisuje, jak vytvořit modul plug-in správy zdrojového kódu, který poskytuje funkce správy zdrojového kódu při použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní správy zdrojového kódu (UI).

- [Referenční informace k sadě Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md) Prezentuje seznam referenčních témat.
