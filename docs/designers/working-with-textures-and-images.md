---
title: Práce s texturami a obrázky
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 110cbbb01f5b86d462a9a5f196735fd4d477fb10
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589861"
---
# <a name="work-with-textures-and-images"></a>Práce s texturami a obrázky

Pomocí editoru obrázků v aplikaci Visual Studio můžete vytvářet a upravovat textury a obrázky. Editor obrázků podporuje bohatou texturu a formáty obrázků, jako jsou ty, které se používají při vývoji aplikací DirectX.

> [!NOTE]
> Editor obrázků nepodporuje obrázky s nízkými barvami, jako jsou ikony nebo kurzory. Chcete-li vytvořit nebo upravit tyto typy obrázků, použijte [Editor obrázků pro ikony (C++)](/cpp/windows/image-editor-for-icons).

## <a name="textures-and-images"></a>Textury a obrázky

Textury a obrázky jsou na základní úrovni pouze tabulky dat, které se používají k poskytnutí vizuálních podrobností v grafických aplikacích. Druh podrobností, které textura nebo obrázek nabízí, závisí na způsobu použití, ale ukázky barev, hodnoty alfa (transparentnost), normály povrchu a hodnoty výšky jsou běžné příklady. Hlavním rozdílem mezi texturou a obrázkem je, že textura je určena k použití společně s znázorněním obrazce – obvykle 3D model – pro vyjádření kompletního objektu nebo scény, ale obrázek je obvykle samostatná reprezentace objektu nebo scény.

Jakákoli textura se dá kódovat a komprimovat různými způsoby, které jsou kolmé k typu dat, která textura obsahuje, nebo k dimenzionálnímu nebo "obrazci" textury. Různé metody kódování a komprese však poskytují lepší výsledky pro různé druhy dat.

Editor obrázků můžete použít k vytváření a úpravám textur a obrázků způsobem, který se podobá ostatním editorům obrázků. Editor obrázků taky poskytuje mipmapping a další funkce pro použití s 3D grafikou a podporuje spoustu vysoce komprimovaných formátů textur s hardwarovou akcelerací, které podporuje DirectX.

Mezi běžné druhy textur patří:

### <a name="texture-maps"></a>Mapy textur

Mapy textur obsahují hodnoty barev, které jsou uspořádány jako jedna, dvě nebo trojrozměrné matice. Slouží k poskytnutí detailů barev ovlivněného objektu. Barvy se běžně kódují pomocí barevných kanálů RGB (červené, zelené, modré) a mohou zahrnovat čtvrtou kanál, alfa, který představuje transparentnost. Méně často se barvy daly kódovat v jiném barevném schématu, nebo čtvrtý kanál může obsahovat jiná data než alfa – například Height.

### <a name="normal-maps"></a>Normální mapy

Normální mapy obsahují normální povrchy. Slouží k poskytnutí podrobností o osvětlení ovlivněného objektu. Normály jsou obvykle kódovány pomocí barevných a zelených a modrých barevných komponent pro ukládání rozměrů vektoru x, y a z. Existují však další kódování, například kódování, která jsou založena na polárních souřadnicích.

### <a name="height-maps"></a>Mapy na výšku

Mapy výšky obsahují data pro pole výšky. Slouží k poskytnutí formy geometrických podrobností o ovlivněném objektu – pomocí kódu shaderu pro výpočet požadovaného účinku, nebo k poskytnutí datových bodů pro použití jako generování terénu. Hodnoty výšky jsou obvykle kódovány pomocí jednoho kanálu v textuře.

### <a name="cube-maps"></a>Mapy krychle

Mapy datových krychlí mohou obsahovat různé typy dat, například barvy nebo normální, ale jsou uspořádány jako šest textur na ploškách datové krychle. Z tohoto důvodu nejsou mapy krychle odebírány zadáním souřadnic textury, ale poskytnutím vektoru, jehož zdrojem je střed datové krychle. vzorek je pořízen v místě, kde vektor protíná datovou krychli. Mapy datových krychlí slouží k zajištění aproximace prostředí, které lze použít k výpočtu odrazů – Toto je známé jako *mapování prostředí*, nebo poskytnutí textury pro kulové objekty s menším narušením než základní, dvourozměrné textury mohou poskytnout.

## <a name="related-topics"></a>Příbuzná témata

|Název|Popis|
|-----------|-----------------|
|[Editor obrázků](../designers/image-editor.md)|Popisuje, jak používat editor obrázků pro práci s texturami a obrázky.|
|[Příklady editoru obrázků](../designers/how-to-create-a-basic-texture.md)|Obsahuje odkazy na témata, která ukazují, jak používat editor obrázků k provádění běžných úloh zpracování obrazu.|
