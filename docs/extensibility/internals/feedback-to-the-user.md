---
title: Zpětná vazba pro uživatele | Microsoft Docs
description: Naučte se, jak poskytnout uživateli vizuální zpětnou vazbu k dostupným funkcím v integrovaném vývojovém prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8f3f79a61729a641ee7c046ddd196a648469fb3
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480522"
---
# <a name="feedback-to-the-user"></a>Zpětná vazba uživateli
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE) je vizuální zpětná vazba týkající se dostupných funkcí založena na aktuálním výběru a kontextu globálního výběru uživatele. V následující tabulce jsou uvedeny funkce, které jsou k dispozici v různých kontextech výběru.

|Kontext výběru|Dostupné funkce|
|-----------------------|-----------------------------|
|IDE – integrované vývojové prostředí|Globální|
|Aktuální sada produktů|Specifické pro produkt|
|Aktivní hierarchie|Specifické pro typ hierarchie|
|Položka aktivní hierarchie|Specifické pro typ položky hierarchie|
|Aktivní dokument|Specifické pro typ dokumentu|
|Nejvyšší okno rozhraní MDI (Multiple Document Interface)|Specifické pro typ okna|
|Aktuální kontext výběru|Konkrétní kontext výběru|

 Pokud potřebujete jenom Surface funkcí, které uživatelé potřebují, a nepřetržitě zajišťovat svůj názor na konzistenci a kontext prostředí, snížíte složitost v integrovaném vývojovém prostředí. Následující pravidla platí při každém otevření okna v integrovaném vývojovém prostředí:

- Pokud okno změní svůj kontext výběru, zpětná vazba výběru je jasně uvedena v okně a dynamické okno **help** , pokud je zobrazeno, je aktualizováno tak, aby odráželo aktuální kontext.

- Pokud okno změní kontext globálního výběru, všechny kontextové nabídky, aktivní okno hierarchie a záhlaví aplikace jsou aktualizovány tak, aby odrážely aktuální kontext.

- Okno by mělo mít vlastnosti povrchu pro aktuální výběr v okně **vlastnosti** a volitelně, pokud je zobrazeno, dialogové okno **stránky vlastností** .

- Pokud okno neumožňuje změnit vlastnosti nebo změnit globální kontext výběru, nemusíte v okně zůstat zpětná vazba výběru, pokud již není aktivním oknem v integrovaném vývojovém prostředí (IDE).

- Všechny okna nástrojů specifické pro dokument by měly průběžně odrážet aktivní dokument.

- Nabídky, panely nástrojů a záhlaví aplikace by měly odrážet nejvyšší klientské okno rozhraní MDI (Multiple Document Interface).

  Pokud je například otevřeno zobrazení HTML **webového formuláře** v projektu webové aplikace Visual Basic a uživatel vybere `<td>` značku, zpětná vazba je poskytována následujícím způsobem:

- Výběr je uveden v aktivním okně a projeví se v okně **vlastnosti** .

- **Sada nástrojů** specifická pro dokument je aktualizována tak, aby odrážela aktivní dokument.

- Zobrazí se panel nástrojů **editoru** a nabídka **tabulka** a záhlaví se aktualizuje tak, aby odráželo okno webového formuláře.

- Okno aktivní hierarchie, které je obvykle **Průzkumník řešení** a jeho záhlaví se aktualizuje tak, aby odráželo aktuální kontext a příkazy místní nabídky **projektu** se teď vztahují na aktivní projekt webové aplikace.

## <a name="see-also"></a>Viz také
- [Výběr a měna v integrovaném vývojovém prostředí](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Objekty kontextu výběru](../../extensibility/internals/selection-context-objects.md)
- [Hierarchie a výběr](../../extensibility/internals/hierarchies-and-selection.md)
