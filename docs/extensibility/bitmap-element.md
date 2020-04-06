---
title: Bitmapový prvek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739997"
---
# <a name="bitmap-element"></a>Bitmapový prvek
Definuje bitmapu. Bitmapa je načtena buď z prostředku, nebo ze souboru.

## <a name="syntax"></a>Syntaxe

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.<br /><br /> Atribut guid pro bitmapu není přidružen k žádné skupině příkazů VSPackage nebo jiné skupině příkazů.  Měla by být jedinečná pro definici bitmapy a neměla by být používána k žádnému jinému účelu.|
|Resid|ID identifikátoru příkazu GUID/ID. Je vyžadován atribut resID nebo href.<br /><br /> Atribut resID je celé ID prostředku, které určuje bitmapový proužek, který má být načten během slučování tabulky příkazů.  Při načítání příkazové tabulky budou bitmapy určené ID prostředku načteny ze zdroje stejného modulu.|
|usedList|Povinné, pokud je přítomen atribut resID. Vybere dostupné obrazy v bitmapovém proužku.|
|Href|Cesta k bitmapě. Je vyžadován atribut resID nebo href.<br /><br /> Cesta zahrnutí je vyhledána pro uvedený soubor obrázku, který je vložen do výsledného binárního souboru.  Během sloučení tabulky příkazů se obraz zkopíruje a není vyžadováno žádné další vyhledávání prostředků nebo zatížení.  Pokud není k dispozici atribut usedList, jsou k dispozici všechny obrázky v pruhu. **Poznámka:**  Obrázky mohou být dodávány v jednom z několika formátů, které obsahují *.bmp*, *.png*a *.gif*.  Dřívější verze kompilátoru nepodporovaly 32bitové bitmapové obrazy, které obsahovaly alfa informace pro částečnou průhlednost. Řešení pro tyto verze je použít formát *PNG.*|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Bitmapový prvek](../extensibility/bitmaps-element.md)|Seskupí bitmapové prvky.|

## <a name="example"></a>Příklad

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
