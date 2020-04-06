---
title: Zpětná vazba pro uživatele | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708404"
---
# <a name="feedback-to-the-user"></a>Zpětná vazba pro uživatele
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE) je vizuální zpětná vazba týkající se dostupných funkcí založena na aktuálním výběru uživatele a kontextu globálního výběru. V následující tabulce jsou uvedeny funkce, které jsou k dispozici v různých kontextech výběru.

|Kontext výběru|Dostupné funkce|
|-----------------------|-----------------------------|
|IDE – integrované vývojové prostředí|Globální|
|Aktuální sada produktů|Specifický produkt|
|Aktivní hierarchie|Specifický typ hierarchie|
|Aktivní položka hierarchie|Specifický typ položky hierarchie|
|Aktivní dokument|Specifický typ dokumentu|
|Okno Rozhraní mDI (Topmost multiple-document)|Specifický typ okna|
|Aktuální kontext výběru|Kontext výběru specifický|

 Pokud pouze povrch funkce, které uživatelé potřebují a neustále poskytují konzistentní výběr a kontext prostředí zpětnou vazbu, snížíte složitost v ide. Následující pravidla platí při každém otevření okna v ide:

- Pokud okno změní kontext výběru, je v okně jasně uvedena zpětná vazba výběru a okno **dynamické nápovědy,** pokud je zobrazeno, je aktualizováno tak, aby odráželo aktuální kontext.

- Pokud okno změní kontext globálního výběru, všechny kontextové nabídky, aktivní okno hierarchie a záhlaví aplikace se aktualizují tak, aby odrážely aktuální kontext.

- Okno by mělo mít vlastnosti povrchu pro aktuální výběr v okně **Vlastnosti** a volitelně, pokud je zobrazeno, dialogové okno **Stránky vlastností.**

- Pokud okno nemá povrch vlastnosti nebo změnit kontext globálního výběru, zpětná vazba výběru by neměla zůstat v okně, pokud již není aktivní okno v rozhraní IDE.

- Všechna okna nástrojů specifických pro dokument by měla průběžně odrážet aktivní dokument.

- Nabídky, panely nástrojů a záhlaví aplikace by měly odrážet nejvyšší okno klienta rozhraní mdi (multiple-document).

  Pokud je například otevřeno zobrazení **HTML webového formuláře** v projektu webové aplikace `<td>` jazyka Visual Basic a uživatel vybere značku, je zpětná vazba poskytnuta následujícím způsobem:

- Výběr je vyznačen v aktivním okně a projeven v okně **Vlastnosti.**

- Panel **nástrojů** specifický pro dokument je aktualizován tak, aby odrážel aktivní dokument.

- Zobrazí se panel nástrojů **Editor** a nabídka **Tabulka** a záhlaví se aktualizuje tak, aby odráželo okno Webový formulář.

- Okno aktivní hierarchie, což je obvykle **Průzkumník řešení**, a jeho aktualizace záhlaví, která odráží aktuální kontext a kontextové příkazy nabídky **Aplikace project,** se nyní vztahují na aktivní projekt webové aplikace.

## <a name="see-also"></a>Viz také
- [Výběr a měna v ide](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Objekty kontextu výběru](../../extensibility/internals/selection-context-objects.md)
- [Hierarchie a výběr](../../extensibility/internals/hierarchies-and-selection.md)
