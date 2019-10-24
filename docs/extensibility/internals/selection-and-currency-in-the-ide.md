---
title: Výběr a měna v integrovaném vývojovém prostředí | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edff400420ca5f0c93e1df85fb9118eee6302d02
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723968"
---
# <a name="selection-and-currency-in-the-ide"></a>Výběr a měna v prostředí IDE
@No__t_0 integrované vývojové prostředí (IDE) udržuje informace o aktuálně vybraných objektech uživatelů pomocí *kontextu*výběru. Pomocí kontextu výběru mohou být VSPackage součástí sledování měn dvěma způsoby:

- Rozšiřováním informací o měnách na rozhraních VSPackage do integrovaného vývojového prostředí (IDE).

- Monitoruje aktuálně aktivní výběry uživatelů v rámci IDE.

## <a name="selection-context"></a>Kontext výběru
 Rozhraní IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] globálně udržuje přehled o měně IDE ve vlastním objektu kontextu globálního výběru. V následující tabulce jsou uvedeny prvky, které tvoří kontext výběru.

|Prvek|Popis|
|-------------|-----------------|
|Aktuální hierarchie|Obvykle aktuální projekt; Aktuální hierarchie s hodnotou NULL označuje, že řešení je zcela aktuální.|
|Aktuální identifikátor ItemID|Vybraná položka v rámci aktuální hierarchie; Pokud je v okně projektu více výběrů, může existovat více aktuálních položek.|
|Aktuální `SelectionContainer`|Obsahuje jeden nebo více objektů, pro které má okno Vlastnosti zobrazit vlastnosti.|

 Prostředí navíc udržuje dva globální seznamy:

- Seznam identifikátorů příkazů aktivního uživatelského rozhraní

- Seznam aktuálně aktivních typů prvků.

### <a name="window-types-and-selection"></a>Typy a výběr oken
 Rozhraní IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Uspořádá okna do dvou obecných typů:

- Okna hierarchie – typ

- Okna s rámečkem, jako jsou například okna nástrojů a dokumentu

  IDE sleduje měnu pro každý z těchto typů oken odlišně.

  Nejběžnějším oknem typu projektu je Průzkumník řešení, který řídí rozhraní IDE. Okno typu projektu sleduje globální hierarchii a identifikátor ItemID kontextu globálního výběru a okno se spoléhá na výběr uživatele k určení aktuální hierarchie. V případě oken typu projekt poskytuje prostředí globální <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> služby, pomocí kterých mohou sady VSPackage monitorovat aktuální hodnoty pro otevřené prvky. Procházení vlastností v prostředí je založené na této globální službě.

  Okna s rámečkem, na druhé straně, použijte DocObject v rámci okna rámce pro vložení hodnoty SelectionContext (Hierarchy/ItemID/SelectionContainer trojice). . Okna s rámečkem používají pro tento účel <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> služby. DocObject může nabízet jenom hodnoty pro kontejner výběru, přičemž místní hodnoty pro hierarchii a ItemID se nezměnily, protože jsou typické pro podřízené dokumenty MDI.

### <a name="events-and-currency"></a>Události a měny
 Mohou nastat dva typy událostí, které mají vliv na fiktivní měnu prostředí:

- Události, které jsou šířeny na globální úrovni a mění kontext výběru rámce okna. Mezi příklady tohoto druhu události patří otevřené podřízené okno MDI, otevřené globální okno nástrojů nebo otevřené okno nástroje typu projekt.

- Události, které mění prvky sledované v kontextu výběru rámce okna. Mezi příklady patří změna výběru v rámci DocObject nebo změna výběru v okně typu projektu.

## <a name="see-also"></a>Viz také:
- [Kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md)
- [Zpětná vazba pro uživatele](../../extensibility/internals/feedback-to-the-user.md)