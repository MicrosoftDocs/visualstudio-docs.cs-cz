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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589861"
---
# <a name="work-with-textures-and-images"></a>Práce s texturami a obrázky

Editor obrázků v sadě Visual Studio můžete použít k vytváření a úpravám textur a obrazů. Editor obrázků podporuje bohaté formáty textur a obrázků, jako jsou ty, které se používají při vývoji aplikací DirectX.

> [!NOTE]
> Editor obrázků nepodporuje obrazy s nízkými barvami, jako jsou ikony nebo kurzory. Chcete-li vytvořit nebo upravit tyto druhy obrázků, použijte [Editor obrázků pro ikony (C++)](/cpp/windows/image-editor-for-icons).

## <a name="textures-and-images"></a>Textury a obrázky

Textury a obrázky jsou na základní úrovni pouze tabulky dat, které se používají k poskytování vizuálních detailů v grafických aplikacích. Druh podrobností, které textura nebo obraz poskytuje, závisí na způsobu jeho použití, ale barevné vzorky, hodnoty alfa (průhlednosti), normály povrchu a hodnoty výšky jsou běžnými příklady. Hlavní rozdíl mezi texturou a obrazem spočine na tom, že textura je určena k použití společně s reprezentací tvaru – obvykle 3D modelu – k vyjádření celého objektu nebo scény, ale obraz je obvykle samostatná reprezentace objektu nebo scény.

Libovolnou texturu lze zakódovat a komprimovat mnoha způsoby, které jsou ortogonové k typu dat, které textura obsahuje, nebo dimenzionalitě nebo "tvaru" textury. Různé metody kódování a komprese však poskytují lepší výsledky pro různé druhy dat.

Editor obrázků můžete použít k vytváření a úpravám textur a obrazů způsobem, který se podobá jiným editorům obrázků. Editor obrázků také poskytuje mipmapping a další funkce pro použití s 3D grafikou a podporuje mnoho vysoce komprimovaných, hardwarově akcelerovaných formátů textur, které rozhraní DirectX podporuje.

Mezi běžné druhy textur patří:

### <a name="texture-maps"></a>Mapy textur

Mapy textur obsahují barevné hodnoty, které jsou uspořádány jako jednorozměrná, dvourozměrná nebo trojrozměrná matice. Používají se k poskytnutí barevných detailů na ovlivněném objektu. Barvy jsou obvykle kódovány pomocí barevných kanálů RGB (červená, zelená, modrá) a mohou obsahovat čtvrtý kanál alfa, který představuje průhlednost. Méně často mohou být barvy kódovány v jiném barevném schématu nebo čtvrtý kanál může obsahovat jiná data než alfa – například výška.

### <a name="normal-maps"></a>Normální mapy

Normální mapy obsahují normály povrchu. Používají se k poskytnutí detailů osvětlení postiženého objektu. Normály jsou obvykle kódovány pomocí červené, zelené a modré barevné komponenty pro uložení rozměrů x, y a z vektoru. Existují však další kódování – například kódování, která jsou založena na polárních souřadnicích.

### <a name="height-maps"></a>Výškové mapy

Výškové mapy obsahují data výškového pole. Používají se k poskytnutí formy geometrických detailů na postiženém objektu – pomocí kódu shaderu k výpočtu požadovaného efektu – nebo k poskytnutí datových bodů pro použití, jako je generování terénu. Hodnoty výšky jsou obvykle kódovány pomocí jednoho kanálu v struktuře.

### <a name="cube-maps"></a>Mapy krychle

Mapy krychle mohou obsahovat různé typy dat – například barvy nebo normály – ale na plochách krychle jsou uspořádány jako šest textur. Z tohoto důvodu mapy krychle nejsou vzorkovány poskytnutím souřadnic textury, ale poskytnutím vektoru, jehož původ je středem krychle; vzorek se odebere v místě, kde vektor protíná krychli. Mapy krychle se používají k aproximaci prostředí, které lze použít k výpočtu odrazů – toto je známé jako *mapování prostředí*– nebo k zajištění textury sférickým objektům s menším zkreslením, než je základní, mohou poskytnout dvourozměrné textury.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Editor obrázků](../designers/image-editor.md)|Popisuje, jak používat Editor obrázků pro práci s texturami a obrazy.|
|[Příklady editoru obrázků](../designers/how-to-create-a-basic-texture.md)|Obsahuje odkazy na témata, která ukazují, jak pomocí editoru obrázků provádět běžné úlohy zpracování obrazu.|
