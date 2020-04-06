---
title: Výběr a měna v ide | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705569"
---
# <a name="selection-and-currency-in-the-ide"></a>Výběr a měna v prostředí IDE
Integrované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vývojové prostředí (IDE) udržuje informace o aktuálně vybraných objektech uživatelů pomocí *kontextu výběru*. S kontextem výběru vSPackages můžete účastnit sledování měny dvěma způsoby:

- Šířením informací o měně o VSPackages do ide.

- Sledováním aktuálně aktivních výběrů uživatelů v rámci ide.

## <a name="selection-context"></a>Kontext výběru
 Ide [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] globálně udržuje informace o měně IDE ve vlastním objektu kontextu globálního výběru. V následující tabulce jsou uvedeny prvky, které tvoří kontext výběru.

|Element|Popis|
|-------------|-----------------|
|Aktuální hierarchie|Obvykle aktuální projekt; aktuální hierarchie NULL označuje, že řešení jako celek je aktuální.|
|Aktuální ItemID|Vybraná položka v aktuální hierarchii; Pokud je v okně projektu více výběrů, může existovat více aktuálních položek.|
|Aktuální`SelectionContainer`|Obsahuje jeden nebo více objektů, pro které by okno Vlastnosti mělo zobrazovat vlastnosti.|

 Prostředí navíc udržuje dva globální seznamy:

- Seznam aktivních identifikátorů příkazů ui

- Seznam aktuálně aktivních typů prvků.

### <a name="window-types-and-selection"></a>Typy a výběr oken
 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uspořádá okna do dvou obecných typů:

- Okna typu Hierarchie

- Okna rámců, například okna nástrojů a dokumentů

  IDE sleduje měnu odlišně pro každý z těchto typů oken.

  Nejběžnější okno typu projektu je průzkumník řešení, který řídí ide. Okno typu projektu sleduje globální hierarchii a ItemID kontextu globálního výběru a okno závisí na výběru uživatele k určení aktuální hierarchie. Pro okna typu projektu prostředí poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>globální službu , pomocí které VSPackages můžete sledovat aktuální hodnoty pro otevřené prvky. Procházení vlastností v prostředí je řízeno touto globální službou.

  Okna rámce, na druhé straně použijte DocObject v okně rámce k push SelectionContext hodnotu (hierarchie/ItemID/SelectionContainer trio). . Okna rámce používají <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> službu pro tento účel. DocObject může tlačit pouze hodnoty pro kontejner výběru, takže místní hodnoty pro hierarchii a ItemID beze změny, jak je typické pro podřízené dokumenty MDI.

### <a name="events-and-currency"></a>Události a měna
 Mohou nastat dva typy událostí, které ovlivňují pojem měny prostředí:

- Události, které jsou šířeny na globální úroveň a změnit kontext výběru rámce okna. Příklady tohoto druhu události zahrnují otevření podřízeného okna MDI, otevírání globálního okna nástroje nebo otevírání okna nástroje typu projektu.

- Události, které mění prvky vysledovat v kontextu výběru rámce okna. Mezi příklady patří změna výběru v rámci docobject nebo změna výběru v okně typu projektu.

## <a name="see-also"></a>Viz také
- [Kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md)
- [Zpětná vazba pro uživatele](../../extensibility/internals/feedback-to-the-user.md)
