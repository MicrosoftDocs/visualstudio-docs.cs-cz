---
title: Bitmap – | Microsoft Docs
description: Bitmap element definuje bitmapu. Bitmapa je načtena buď z prostředku, nebo ze souboru. Tento článek obsahuje příklad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c8f3daf25a3ffe025bcdef65dbaa6def942d0fb4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903317"
---
# <a name="bitmap-element"></a>Bitmap – element
Definuje rastrový obrázek. Bitmapa je načtena buď z prostředku, nebo ze souboru.

## <a name="syntax"></a>Syntax

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.<br /><br /> Atribut guid bitmapy není přidružený k žádnému balíčku VSPackage ani jiné skupině příkazů.  Měl by být jedinečný pro definici rastrového obrázku a neměl by být používán k žádnému jinému účelu.|
|Resid|ID identifikátoru příkazu GUID/ID. Vyžaduje se buď resID, nebo atribut href.<br /><br /> Atribut resID je ID prostředku celého čísla, které určuje pruh rastrového obrázku, který se má načíst během slučování tabulky příkazů.  Při načítání tabulky příkazů se rastrové obrázky určené ID prostředku načtou z prostředku stejného modulu.|
|usedList|Vyžaduje se, pokud existuje atribut resID. Vybere dostupné obrázky v pruhu rastrových obrázků.|
|Href|Cesta k bitmapě. Vyžaduje se buď resID, nebo atribut href.<br /><br /> Cesta k zahrnutí vyhledá označený soubor obrázku, který je vložen do výsledného binárního souboru.  Během sloučení tabulky příkazů se image zkopíruje a nevyžaduje se žádné další vyhledávání ani načítání prostředků.  Pokud atribut usedList není k dispozici, jsou k dispozici všechny obrázky v pruhu. **Poznámka:**  Obrázky mohou být dodány v jednom z několika formátů, mezi *které patří.bmp*, *.png* a *.gif*.  Starší verze kompilátoru nepodporují 32bitové rastrové obrázky, které měly informace alfa pro částečnou průhlednost. Alternativním řešením pro tyto verze je použití *.png* formátu.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Bitmaps – element](../extensibility/bitmaps-element.md)|Seskupí elementy bitmapy.|

## <a name="example"></a>Příklad

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Viz také
- [Visual Studio souborů tabulky příkazů (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
