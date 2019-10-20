---
title: Práce s texturami a obrázky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 93813aa734c615e7f045c98c776e600be4ee3fab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663940"
---
# <a name="working-with-textures-and-images"></a>Práce s texturami a obrázky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K vytváření a úpravám textur a imagí můžete použít Editor obrázků v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Editor obrázků podporuje bohatou texturu a formáty obrázků, jako jsou ty, které se používají při vývoji aplikací DirectX.

> [!NOTE]
> Editor obrázků nepodporuje obrázky s nízkými barvami, jako jsou ikony nebo kurzory. Chcete-li vytvořit nebo upravit tyto typy obrázků, použijte [Editor obrázků pro ikony](https://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd).

## <a name="textures-and-images"></a>Textury a obrázky
 Textury a obrázky jsou na základní úrovni pouze tabulky dat, které se používají k poskytnutí vizuálních podrobností v grafických aplikacích. Druh podrobností, které textura nebo obrázek nabízí, závisí na způsobu použití, ale ukázky barev, hodnoty alfa (transparentnost), normály povrchu a hodnoty výšky jsou běžné příklady. Základní rozdíl mezi texturou a obrázkem spočívá v tom, že textura je určena k použití společně s znázorněním tvaru – typicky 3D model – pro vyjádření kompletního objektu nebo scény, ale obrázek je obvykle samostatná reprezentace objektu nebo scény. .

 Mezi běžné druhy textur patří:

 Mapy textury mapy textur obsahují hodnoty barev, které jsou uspořádány jako jedna, dvě nebo trojrozměrné matice. Slouží k poskytnutí detailů barev ovlivněného objektu. Barvy se běžně kódují pomocí barevných kanálů RGB (červené, zelené, modré) a mohou zahrnovat čtvrtou kanál, alfa, který představuje transparentnost. Méně často se barvy daly kódovat v jiném barevném schématu, nebo čtvrtý kanál může obsahovat jiná data než alfa – například Height.

 Normální mapy normálních map obsahují normální povrchy. Slouží k poskytnutí podrobností o osvětlení ovlivněného objektu. Normály jsou obvykle kódovány pomocí barevných a zelených a modrých barevných komponent pro ukládání rozměrů vektoru x, y a z. Existují však další kódování, například kódování, která jsou založena na polárních souřadnicích.

 Mapy výšky mapy na výšku obsahují data pro pole výšky. Slouží k poskytnutí formy geometrických podrobností o ovlivněném objektu – pomocí kódu shaderu pro výpočet požadovaného účinku, nebo k poskytnutí datových bodů pro použití jako generování terénu. Hodnoty výšky jsou obvykle kódovány pomocí jednoho kanálu v textuře.

 Mapy krychle mapy krychle mohou obsahovat různé typy dat, například barvy nebo normální, ale jsou uspořádány jako šest textur na plochách datové krychle. Z tohoto důvodu nejsou mapy krychle odebírány zadáním souřadnic textury, ale poskytnutím vektoru, jehož zdrojem je střed datové krychle. vzorek je pořízen v místě, kde vektor protíná datovou krychli. Mapy datových krychlí slouží k zajištění aproximace prostředí, které lze použít k výpočtu odrazů – Toto je známé jako *mapování prostředí*, nebo poskytnutí textury pro kulové objekty s menším narušením než na úrovni Basic, dvourozměrných textur může sdělit.

 Jakákoli textura se dá kódovat a komprimovat různými způsoby, které jsou kolmé k typu dat, která textura obsahuje, nebo k dimenzionálnímu nebo "obrazci" textury. Různé metody kódování a komprese však poskytují lepší výsledky pro různé druhy dat.

 Editor obrázků můžete použít k vytváření a úpravám textur a obrázků způsobem, který se podobá ostatním editorům obrázků. Editor obrázků taky poskytuje mipmapping a další funkce pro použití s 3D grafikou a podporuje spoustu vysoce komprimovaných formátů textur s hardwarovou akcelerací, které podporuje DirectX.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Editor obrázků](../designers/image-editor.md)|Popisuje, jak používat editor obrázků pro práci s texturami a obrázky.|
|[Příklady editoru obrázků](../designers/image-editor-examples.md)|Obsahuje odkazy na témata, která ukazují, jak používat editor obrázků k provádění běžných úloh zpracování obrazu.|
