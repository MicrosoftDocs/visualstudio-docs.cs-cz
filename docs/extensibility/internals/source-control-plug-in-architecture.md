---
title: Architektura modulu plug-in správy zdrojových kódů | Microsoft Docs
description: Přečtěte si, jak přidat podporu správy zdrojového kódu do integrovaného vývojového prostředí sady Visual Studio implementací a připojením modulu plug-in správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e154e91ce552df9e54d45ea9210a0679edae5f28
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878063"
---
# <a name="source-control-plug-in-architecture"></a>Architektura modulu plug-in správy zdrojového kódu
Můžete přidat podporu správy zdrojového kódu do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE) implementací a připojením modulu plug-in správy zdrojového kódu. Rozhraní IDE se připojí k modulu plug-in správy zdrojového kódu prostřednictvím dobře definovaného rozhraní API správy zdrojového kódu Plug-In. Rozhraní IDE zpřístupňuje funkce správy verzí systému správy zdrojového kódu tím, že poskytuje uživatelské rozhraní (UI), které se skládá z panelů nástrojů a příkazů nabídky. Modul plug-in správy zdrojových kódů implementuje funkce správy zdrojového kódu.

## <a name="source-control-plug-in-resources"></a>Prostředky modulu plug-in správy zdrojového kódu
 Modul plug-in správy zdrojových kódů poskytuje prostředky, které vám pomůžou vytvořit a připojit vaši aplikaci pro správu verzí k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Modul plug-in správy zdrojových kódů obsahuje specifikaci rozhraní API, kterou musí implementovat modul plug-in správy zdrojových kódů, aby bylo možné je integrovat do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE). Obsahuje také ukázku kódu (napsané v jazyce C++), která implementuje modul plug-in správy zdrojových kódů demonstrující implementaci základních funkcí, které jsou kompatibilní s rozhraním API modulu plug-in správy zdrojového kódu.

 Specifikace rozhraní API modulu plug-in správy zdrojových kódů umožňuje využít libovolný systém správy zdrojů podle vašeho výběru, pokud vytvoříte knihovnu DLL správy zdrojového kódu s požadovanou sadou funkcí implementovaných v souladu s rozhraním API modulu plug-in správy zdrojového kódu.

## <a name="components"></a>Komponenty
 Balíček pro správu zdrojového kódu v diagramu je komponenta rozhraní IDE, která překládá požadavek uživatele na operaci správy zdrojů do volání funkce podporovaného modulem plug-in správy zdrojových kódů. Aby k tomu mohlo dojít, rozhraní IDE a modul plug-in správy zdrojových kódů musí mít účinný dialog, který předává informace mezi IDE a modulem plug-in. Aby se toto dialogové okno probíhat, musí oba mluvit stejný jazyk. Rozhraní API pro modul plug-in správy zdrojových kódů, které je uvedené v této dokumentaci, je běžný slovník pro tento Exchange.

 ![Diagram architektury správy zdrojového kódu](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagram architektury znázorňující interakci mezi modulem plug-in VS and Source Control

 Jak je znázorněno v diagramu architektury, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí, označené jako vs Shell v diagramu, hostuje pracovní projekty uživatele a přidružené komponenty, jako jsou editory a Průzkumník řešení. Balíček adaptéru správy zdrojového kódu zpracovává interakci mezi rozhraním IDE a modulem plug-in správy zdrojových kódů. Balíček adaptéru správy zdrojového kódu poskytuje vlastní uživatelské rozhraní správy zdrojového kódu. Je uživatelské rozhraní nejvyšší úrovně, se kterým uživatel pracuje, aby bylo možné zahájit a definovat rozsah operace správy zdrojových kódů.

 Modul plug-in správy zdrojových kódů může mít vlastní uživatelské rozhraní, které se může skládat ze dvou částí, jak je znázorněno na obrázku. Pole označený jako uživatelské rozhraní dodavatele představuje vlastní prvky uživatelského rozhraní, které jako tvůrce modulu plug-in správy zdrojového kódu poskytují. Tyto prvky jsou zobrazeny přímo modulem plug-in správy zdrojového kódu, když uživatel vyvolá pokročilou operaci správy zdrojového kódu. Box s označením "pomocné uživatelské rozhraní" je sada funkcí uživatelského rozhraní modulu plug-in správy zdrojových kódů, které jsou nepřímo vyvolány prostřednictvím integrovaného vývojového prostředí. Modul plug-in správy zdrojových kódů předává zprávy související s uživatelským rozhraním do integrovaného vývojového prostředí prostřednictvím speciálních funkcí zpětného volání poskytovaných IDE. Uživatelské rozhraní pomocníka usnadňuje plynulou integraci s rozhraním IDE (často prostřednictvím použití **rozšířeného** tlačítka), a proto nabízí ucelené prostředí pro koncové uživatele.

 Modul plug-in správy zdrojových kódů nemůže v prostředí provádět změny [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a v důsledku toho buď na balíček adaptéru správy zdrojového kódu, nebo na uživatelské rozhraní správy zdrojového kódu poskytované rozhraním IDE. Musí využít maximální využití flexibility prostřednictvím implementace různých funkcí rozhraní API modulu plug-in správy zdrojového kódu, které přispívají k integrovanému prostředí pro koncového uživatele. Referenční část dokumentace k rozhraní API modulu plug-in správy zdrojových kódů obsahuje informace pro některé pokročilé možnosti modulu plug-in správy zdrojového kódu. Aby bylo možné tyto funkce zneužít, musí modul plug-in správy zdrojových kódů deklarovat své pokročilé možnosti na rozhraní IDE během inicializace a musí implementovat konkrétní pokročilé funkce pro každou schopnost.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md)
- [Glosář](../../extensibility/source-control-plug-in-glossary.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
