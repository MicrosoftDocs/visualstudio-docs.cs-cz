---
title: Architektura modulu plug-in správy zdrojového kódu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705111"
---
# <a name="source-control-plug-in-architecture"></a>Architektura modulu plug-in správy zdrojového kódu
Podporu správy zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] můžete přidat do integrovaného vývojového prostředí (IDE) implementací a připojením modulu plug-in správy zdrojového kódu. Rozhraní IDE se připojuje k modulu plug-in správy zdrojového kódu prostřednictvím dobře definovaného rozhraní plug-in správy zdrojového kódu. Rozhraní IDE zveřejňuje funkce správy verzí systému správy zdrojového kódu tím, že poskytuje uživatelské rozhraní (UI), které se skládá z panelů nástrojů a příkazů nabídky. Modul plug-in správy zdrojového kódu implementuje funkci správy zdrojového kódu.

## <a name="source-control-plug-in-resources"></a>Zdrojem dat plug-in prostředky
 Modul plug-in správy zdrojového kódu poskytuje prostředky, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pomáhají vytvářet a připojovat aplikaci pro správu verzí k ide. Modul plug-in správy zdrojového kódu obsahuje specifikaci rozhraní API, která musí být [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementována modulem plug-in správy zdrojového kódu, aby mohla být integrována do integrovaného vývojového prostředí. Obsahuje také ukázku kódu (napsanou v jazyce C++), která implementuje modul plug-in správy zdrojového kódu, který demonstruje implementaci základních funkcí kompatibilních s rozhraním API modulu plug-in správy zdrojového kódu.

 Specifikace rozhraní plug-in source control umožňuje využít libovolný systém správy zdrojového kódu podle vašeho výběru, pokud vytvoříte datovou dll pro slučování dat s požadovanou sadou funkcí implementovaných v souladu s rozhraním API modulu plug-in správy zdrojového kódu.

## <a name="components"></a>Komponenty
 Balíček adaptéru správy zdrojového kódu v diagramu je součástí rozhraní IDE, které převádí požadavek uživatele na operaci správy zdrojového kódu na volání funkce podporované modulem plug-in správy zdrojového kódu. Aby k tomu došlo, ide a modul plug-in správy zdrojového kódu musí mít efektivní dialogové okno, které předává informace tam a zpět mezi ide a modul plug-in. Aby k tomuto dialogu došlo, musí oba mluvit stejným jazykem. Rozhraní plug-in source control rozhraní API popsané v této dokumentaci je běžnýslovník pro tuto výměnu.

 ![Diagram architektury správy zdrojového kódu](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagram architektury znázorňující interakci mezi modulem Plug-in VS a modulem plug-in správy zdrojového kódu

 Jak je znázorněno v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagramu architektury, prostředí, označené jako VS shell v diagramu, hostuje pracovní projekty uživatele a přidružené součásti, jako jsou editory a Průzkumník řešení. Balíček adaptéru správy zdrojového kódu zpracovává interakci mezi ide a modul plug-in řízení zdrojového kódu. Balíček adaptéru správy zdrojového kódu poskytuje vlastní ovládací prvek zdrojového kódu. Jedná se o uživatelské rozhraní nejvyšší úrovně, se kterým uživatel spolupracuje, aby mohl zahájit a definovat rozsah operace správy zdrojového kódu.

 Modul plug-in správy zdrojového kódu může mít vlastní ui, které se může skládat ze dvou částí, jak je znázorněno na obrázku. Pole označené "Uživatelské rozhraní dodavatele" představuje vlastní prvky uživatelského rozhraní, které jako tvůrce modulu plug-in správy zdrojového kódu poskytnete. Ty jsou zobrazeny přímo modulu plug-in správy zdrojového kódu, když uživatel vyvolá pokročilou operaci správy zdrojového kódu. Pole označené "Helper UI" je sada funkcí modulu plug-in správy zdrojového kódu, které jsou nepřímo vyvolány prostřednictvím ide. Modul plug-in správy zdrojového kódu předává zprávy související s uznatým ide prostřednictvím speciálních funkcí zpětného volání poskytované hodem IDE. Pomocné uživatelské rozhraní usnadňuje bezproblémovější integraci s rozhraním IDE (často pomocí tlačítka **Advanced)** a poskytuje tak jednotnější prostředí pro koncové uživatele.

 Modul plug-in správy zdrojového [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kódu nemůže provádět změny prostředí a v důsledku toho balíček adaptéru pro řízení zdrojového kódu nebo u ovládacího prvku zdroje poskytované prostředím IDE. Musí maximálně využít flexibilitu nabízenou implementací různých funkcí rozhraní API modulu plug-in správy zdrojového kódu, které přispívají k integrovanému prostředí pro koncového uživatele. Referenční část dokumentace rozhraní plug-in správy zdrojového kódu obsahuje informace o některých pokročilých funkcích modulu plug-in správy zdrojového kódu. Chcete-li tyto funkce využít, musí modul plug-in správy zdrojového kódu deklarovat své rozšířené funkce ide během inicializace a musí implementovat specifické pokročilé funkce pro každou funkci.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md)
- [Glosář](../../extensibility/source-control-plug-in-glossary.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
