---
title: 'Testovací oblast 8: přepínání modulů plug-in | Microsoft Docs'
description: Tato testovací oblast správy zdrojového kódu poskytuje testovací případy pro proces výběru, který modul plug-in použije pro správu zdrojového kódu řešení v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dbc6b9646bcdec8cbdfae9d262397eb0ff74bdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090769"
---
# <a name="test-area-8-plug-in-switching"></a>Testovací oblast 8: Přepínání modulů plug-in
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Integrované vývojové prostředí (IDE) má uživatelské rozhraní (UI), které umožňuje změnit aktuální modul plug-in správy zdrojových kódů. Tato testovací oblast poskytuje testovací případy pro proces výběru, který modul plug-in bude použit pro správu zdrojového kódu řešení.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]V testovacích případech se používají následující cesty nabídky integrovaného vývojového prostředí.

- Aktuální modul plug-in správy zdrojových kódů: možnosti **nástrojů**  ->    ->  výběr modulu plug-in **správy zdrojového kódu**  ->  .

- Změnit vazbu správy zdrojového kódu **:** Změna správy zdrojového kódu  ->    ->  ...

## <a name="common-expected-behavior"></a>Obvyklé očekávané chování
 Změna modulu plug-in správy zdrojového kódu pro řešení je možná bez ukončení sady Visual Studio nebo opětovného načtení řešení. Kromě toho se aktuální modul plug-in správy zdrojových kódů automaticky změní na ten, který řešení používá, když je toto řešení načteno.

## <a name="test-cases"></a>Testovací případy
 Níže jsou uvedené konkrétní testovací případy pro přepínání v oblasti testu modulu plug-in.

### <a name="case-8a-automatic-change"></a>Případ 8a: Automatická změna

#### <a name="expected-behavior"></a>Očekávané chování
 Když uživatel načte řešení, které je pod správou zdrojových kódů, řešení se načte automaticky a příslušný modul plug-in správy zdrojových kódů se vybere jako aktuální.

| Akce | Testovací kroky | Očekávané výsledky k ověření |
| - | - | - |
| Automatická změna modulu plug-in správy zdrojového kódu | 1. v části test jako aktuální vyberte modul plug-in (možnosti **nástrojů**  ->    ->  výběr modulu plug-in **správy zdrojového kódu**  ->  ).<br />2. Vytvořte nový projekt.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Vyberte jiný modul plug-in (například [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />5. přijetí výzvy k uvolnění řešení.<br />6. znovu otevřete řešení z disku. | Řešení je otevřeno.<br /><br /> Modul plug-in v rámci testu je aktuálním modulem plug-in pro správu zdrojového kódu. |

### <a name="case-8b-solution-based-change"></a>Případ 8B: Změna založená na řešení

#### <a name="expected-behavior"></a>Očekávané chování
 K řešení může být změněn modul plug-in správy zdrojového kódu.

| Akce | Testovací kroky | Očekávané výsledky k ověření |
|----------------------------------| - | - |
| Změna modulu plug-in pro řešení | 1. v části test jako aktuální vyberte modul plug-in (možnosti **nástrojů**  ->    ->  výběr modulu plug-in **správy zdrojového kódu**  ->  ).<br />2. Vytvořte nový projekt a řešení.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. zrušte vazbu řešení ze správy zdrojového kódu (pomocí dialogového okna **změnit správu zdrojového kódu** ).<br />5. Vyberte jiný modul plug-in (například [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />6. Pokud je toto řešení načtené, načtěte ho z disku.<br />7. Přidejte řešení do správy zdrojového kódu.<br />8. zrušte vazbu řešení ze správy zdrojového kódu (pomocí dialogového okna **změnit správu zdrojového kódu** ).<br />9. v části test znovu vyberte modul plug-in.<br />10. znovu načíst řešení z disku při uvolnění<br />11. Připojte řešení k původnímu umístění (pomocí dialogového okna **změnit správu zdrojového kódu** ). | Řešení se přidá do správy zdrojového kódu pomocí vybraného modulu plug-in. |

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
