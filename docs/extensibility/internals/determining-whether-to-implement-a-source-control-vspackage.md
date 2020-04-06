---
title: Určení, zda implementovat zdrojového kódu VSPackage | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708725"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Určit, zda chcete implementovat zdrojového ovládacího prvku VSPackage
Tato část zpracovává volby modulů plug-in správy zdrojového kódu a správy zdrojového kódu VSPackages pro rozšíření řešení správy zdrojového kódu a poskytuje obecné pokyny pro výběr vhodné cesty integrace.

## <a name="small-source-control-solution-with-limited-resources"></a>Řešení správy malých zdrojů s omezenými zdroji
 Pokud máte omezené prostředky a nelze je zatížit režií psaní balíčku správy zdrojového kódu, můžete vytvořit moduly plug-in moduly api založené na modulu API správy zdrojového kódu. Další informace naleznete v [tématu Registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Řešení pro slučovací řízení velkých zdrojů s bohatou sadou funkcí
 Pokud chcete implementovat řešení správy zdrojového kódu, který poskytuje bohatý zdroj ový model správy, který není dostatečně zachycen pomocí rozhraní API modulu plug-in správy zdrojového kódu, můžete považovat balíček správy zdrojového kódu jako cestu integrace. To platí zejména v případě, že byste raději nahradit balíček adaptéru správy zdrojového kódu (který komunikuje s moduly plug-in správy zdrojového kódu a poskytuje základní zdroj ovládacího prvku uI) s vlastní tak, že můžete zpracovat události správy zdrojového kódu vlastním způsobem. Pokud již máte uspokojivé uživatelské nastavení správy zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]a chcete zachovat toto prostředí v , možnost balíčku správy zdrojového kódu umožňuje provést právě to. Balíček správy zdrojového kódu není obecný a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je určen výhradně pro použití s ide.

 Pokud chcete implementovat řešení správy zdrojového kódu, které poskytuje flexibilitu a bohatší kontrolu nad logikou správy zdrojového kódu a ui, můžete upřednostňovat směrování integrace balíčku správy zdrojového kódu. Můžete:

1. Zaregistrujte si vlastní zdrojového ovládacího prvku VSPackage (viz [Registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Nahraďte výchozí uživatelské rozhraní správy zdrojového kódu vlastním uživatelským rozhraním (viz [Vlastní uživatelské rozhraní](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Určete glyfy, které mají být použity, a zpracovat události glyfů Průzkumníka řešení (viz [Kontrola glyfů).](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Zpracovat události úprav dotazu a ukládání dotazů (viz [Úprava dotazu při ukládání dotazu).](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

## <a name="see-also"></a>Viz také
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
