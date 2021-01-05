---
title: Výběr a měna v integrovaném vývojovém prostředí | Microsoft Docs
description: Přečtěte si, jak se v rámci sledování měn přijímají VSPackage. Integrované vývojové prostředí sady Visual Studio uchovává informace o aktuálně vybraných objektech pomocí kontextu výběru.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b2d745619be8bff77503bc14a1d7a87d84cc7864
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875593"
---
# <a name="selection-and-currency-in-the-ide"></a>Výběr a měna v prostředí IDE
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Integrované vývojové prostředí (IDE) udržuje informace o aktuálně vybraných objektech uživatelů pomocí *kontextu* výběru. Pomocí kontextu výběru mohou být VSPackage součástí sledování měn dvěma způsoby:

- Rozšiřováním informací o měnách na rozhraních VSPackage do integrovaného vývojového prostředí (IDE).

- Monitoruje aktuálně aktivní výběry uživatelů v rámci IDE.

## <a name="selection-context"></a>Kontext výběru
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Integrované vývojové prostředí (IDE) globálně udržuje přehled o měně IDE ve vlastním objektu kontextu globálního výběru. V následující tabulce jsou uvedeny prvky, které tvoří kontext výběru.

|Element|Popis|
|-------------|-----------------|
|Aktuální hierarchie|Obvykle aktuální projekt; Aktuální hierarchie s hodnotou NULL označuje, že řešení je zcela aktuální.|
|Aktuální identifikátor ItemID|Vybraná položka v rámci aktuální hierarchie; Pokud je v okně projektu více výběrů, může existovat více aktuálních položek.|
|Aktivní `SelectionContainer`|Obsahuje jeden nebo více objektů, pro které má okno Vlastnosti zobrazit vlastnosti.|

 Prostředí navíc udržuje dva globální seznamy:

- Seznam identifikátorů příkazů aktivního uživatelského rozhraní

- Seznam aktuálně aktivních typů prvků.

### <a name="window-types-and-selection"></a>Typy a výběr oken
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Rozhraní IDE Uspořádá okna do dvou obecných typů:

- Okna hierarchie – typ

- Okna s rámečkem, jako jsou například okna nástrojů a dokumentu

  IDE sleduje měnu pro každý z těchto typů oken odlišně.

  Nejběžnějším oknem typu projektu je Průzkumník řešení, který řídí rozhraní IDE. Okno typu projektu sleduje globální hierarchii a identifikátor ItemID kontextu globálního výběru a okno se spoléhá na výběr uživatele k určení aktuální hierarchie. Pro okna typu projekt poskytuje prostředí globální službu <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> , pomocí které mohou sady VSPackage monitorovat aktuální hodnoty pro otevřené prvky. Procházení vlastností v prostředí je založené na této globální službě.

  Okna s rámečkem, na druhé straně, použijte DocObject v rámci okna rámce pro vložení hodnoty SelectionContext (Hierarchy/ItemID/SelectionContainer trojice). . Okna s rámečkem používají <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> pro tento účel službu. DocObject může nabízet jenom hodnoty pro kontejner výběru, přičemž místní hodnoty pro hierarchii a ItemID se nezměnily, protože jsou typické pro podřízené dokumenty MDI.

### <a name="events-and-currency"></a>Události a měny
 Mohou nastat dva typy událostí, které mají vliv na fiktivní měnu prostředí:

- Události, které jsou šířeny na globální úrovni a mění kontext výběru rámce okna. Mezi příklady tohoto druhu události patří otevřené podřízené okno MDI, otevřené globální okno nástrojů nebo otevřené okno nástroje typu projekt.

- Události, které mění prvky sledované v kontextu výběru rámce okna. Mezi příklady patří změna výběru v rámci DocObject nebo změna výběru v okně typu projektu.

## <a name="see-also"></a>Viz také
- [Kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md)
- [Zpětná vazba pro uživatele](../../extensibility/internals/feedback-to-the-user.md)
