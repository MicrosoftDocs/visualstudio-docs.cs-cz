---
title: Kreslení tvarů a cest | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9eba4e5bfef052f7a82c3148f5628eff9413180
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542204"
---
# <a name="draw-shapes-and-paths"></a>Kreslení tvarů a cest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V Návrhář XAML je *tvar* přesně to, co byste očekávali. Například: obdélník, kruh nebo elipsa. *Cesta* je flexibilnější verze tvaru. Můžete provádět akce, jako je jejich změna tvaru nebo jejich kombinování, aby bylo možné vytvořit nové tvary.

 Obrazce a cesty používají vektorové grafiky, aby se na displeje s vysokým rozlišením správně škálovat. Pokud se chcete dozvědět více o vektorové grafické prvky, přečtěte si téma [co jsou vektorová grafika](https://www.youtube.com/watch?v=MoCSwF0n-io) nebo [Vektorová grafika](https://www.webopedia.com/TERM/V/vector_graphics.html).

 **V tomto tématu:**

- [Nakreslit obrazec](#Shape)

- [Nakreslit cestu](#Path)

- [Převod tvaru na cestu](#Convert)

- [Kombinovat cesty](#Combine)

- [Vytvořit složenou cestu](#Compound)

- [Vytvořit ořezovou cestu](#Clipping)

## <a name="draw-a-shape"></a><a name="Shape"></a>Nakreslit obrazec
 Tvary můžete najít na panelu **aktiva** .

 ![Kategorie Shapes na panelu aktiva](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")

 Přetáhněte libovolný tvar, který chcete na návrhovou plochu. Pak můžete použít táhla obrazce ke změně měřítka, otočení, přesunutí nebo zkosení obrazce.

 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")

## <a name="draw-a-path"></a><a name="Path"></a>Nakreslit cestu
 Cesta je řada propojených čar a křivek. Použijte cestu k vytvoření zajímavých tvarů, které nejsou k dispozici na panelu **aktiva** .

 Můžete nakreslit cestu pomocí čáry, pera nebo tužky. Tyto nástroje můžete najít na panelu **nástroje** .

 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")

### <a name="draw-a-straight-line"></a>Nakreslení rovné čáry
 Použijte nástroj **pero** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") nebo nástroj **čára** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf") .

 **Použití nástroje pero**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")

 Na návrhové ploše klikněte jednou, abyste definovali počáteční bod, a potom klikněte znovu na definovat konec řádku.

 **Pomocí nástroje čára**![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")

 Na návrhové ploše přetáhněte z místa, kde má být řádek spuštěn, a potom uvolněte místo, kde má řádek končit.

### <a name="draw-a-curve"></a>Nakreslení křivky
 Použijte nástroj **pero** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") .

 Na návrhové ploše klikněte jednou a definujte počáteční bod řádku a potom klikněte a přetáhněte ukazatel myši k vytvoření požadované křivky.

 Pokud chcete cestu zavřít, klikněte na první bod na řádku.

### <a name="change-the-shape-of-a-curve"></a>Změna tvaru křivky
 Použijte nástroj **přímý výběr** ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362") .

 Klikněte na tvar a potom přetažením libovolného bodu na tvaru změňte obrazce křivky.

### <a name="draw-a-free-form-path"></a>Nakreslení cesty volného tvaru
 Použijte nástroj **Tužka** ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd") .

 Na návrhové ploše nakreslete cestu k volnému formátu stejným způsobem jako při použití skutečné tužky.

### <a name="remove-part-of-a-path"></a>Odebrání části cesty
 Použijte nástroj **přímý výběr** ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362") .

 Vyberte cestu obsahující segment, který chcete odstranit, a potom klikněte na tlačítko **Odstranit** .

### <a name="remove-a-point-in-a-path"></a>Odebrání bodu v cestě
 Použijte nástroj **Výběr** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") a nástroj **pero** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") .

 Pomocí nástroje **Výběr** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") Vyberte cestu. Pak pomocí nástroje **pero** klikněte na ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") bod, který chcete odebrat.

### <a name="add-a-point-to-a-path"></a>Přidat bod do cesty
 Použijte nástroj **Výběr** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") a nástroj **pero** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") .

 Pomocí nástroje **Výběr** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") Vyberte cestu. Pomocí nástroje **pero** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") klikněte na libovolné místo na cestě, kam chcete bod přidat.

## <a name="convert-a-shape-to-a-path"></a><a name="Convert"></a>Převod tvaru na cestu
 Chcete-li upravit tvar stejným způsobem, jakým jste změnili cestu, převeďte tvar na cestu.

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících s cestami: převod tvaru na cestu](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

## <a name="combine-paths"></a><a name="Combine"></a>Kombinovat cesty
 Cesty a tvary můžete zkombinovat do jedné cesty.

 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-a338-4ef4-96c5-dae51cc1ca8a")

|Image|Popis|Image|Popis|
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|Dva obrazce před kombinováním|![](../designers/media/b1-4.png "B1_4")|Krývají|
|![](../designers/media/b1-2.png "B1_2")|Toho|![](../designers/media/b1-5.png "B1_5")|Vyloučit překryv|
|![](../designers/media/b1-3.png "B1_3")|Dělení|![](../designers/media/b1-6.png "B1_6")|Odčítání|

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících s cestami: kombinování cest](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a><a name="Compound"></a>Vytvořit složenou cestu
 Když vytváříte složenou cestu, všechny protínající se části cest odečtou od výsledku a výsledná cesta přebírá vizuální vlastnosti nejspodnější cesty.

 Složenou cestu můžete kdykoli po vytvoření rozdělit do všech časových teček.

 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících s cestami: vytvořit složenou cestu](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a><a name="Clipping"></a>Vytvořit ořezovou cestu
 Ořezová cesta je cesta nebo tvar, který je použit na jiný objekt, skrývání částí maskovaného objektu, které spadají mimo ořezovou cestu.

 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících s cestami: vytvořit ořezovou cestu](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>Viz také
 [Vytvoření uživatelského rozhraní pomocí nástroje Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
