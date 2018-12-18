---
title: Kreslení tvarů a cest | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0f59ecbdf9e69093d5c445cdb6d4780eb3b6f86e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188185"
---
# <a name="draw-shapes-and-paths"></a>Kreslení tvarů a cest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V Návrháři XAML *tvar* je přesně to, co byste očekávali. Příklad: obdélník, kruh nebo elipsu. A *cesta* je flexibilnější verze tvaru. Můžete třeba je změnit tvar nebo kombinovat společně na formulář nové obrazce.  
  
 Tvarů a cest používá vektorovou grafiku, takže jejich škálování i na displejích s vysokým rozlišením. Pokud chcete získat další informace o vektorové grafiky, naleznete v tématu [co jsou vektorové grafiky](https://www.youtube.com/watch?v=MoCSwF0n-io) nebo [vektorové grafiky](http://www.webopedia.com/TERM/V/vector_graphics.html).  
  
 **V tomto tématu:**  
  
-   [Nakreslit obrazec](#Shape)  
  
-   [Nakreslení cesty](#Path)  
  
-   [Převod tvaru na cestu](#Convert)  
  
-   [Spojit cesty](#Combine)  
  
-   [Vytvořit složenou cestu](#Compound)  
  
-   [Vytvořit ořezovou cestu](#Clipping)  
  
##  <a name="Shape"></a> Nakreslit obrazec  
 Tvary můžete najít **prostředky** panelu.  
  
 ![Kategorii prvků na panelu aktiva](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")  
  
 Žádný obrazec, který chcete přetáhněte na návrhovou plochu. Pak můžete popisovače obrazce škálování, otáčet, přesunout nebo zkosení tvar.  
  
 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")  
  
##  <a name="Path"></a> Nakreslení cesty  
 Cesta je řada připojených čar a křivek. Můžete vytvářet zajímavé tvary, které nejsou k dispozici v cestu **prostředky** panelu.  
  
 Nakreslení cesty pomocí spojnicovém, psaní perem nebo tužky. Můžete najít v těchto nástrojů **nástroje** panelu.  
  
 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")  
  
### <a name="draw-a-straight-line"></a>Nakreslení rovné čáry  
 Použití **pera** nástroj ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54"), nebo **řádku** nástroj ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf").  
  
 **S nástrojem pero** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")  
  
 Na návrhové ploše kliknutím definujte počáteční bod a poté opětovným kliknutím definujte konec řádku.  
  
 **Pomocí nástroje řádku** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")  
  
 Na návrhové ploše přetáhnout z kde chcete řádek, který spustí a uvolněte v místě, kde chcete řádek na konec.  
  
### <a name="draw-a-curve"></a>Nakreslení křivky  
 Použití **pera** nástroj ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Na návrhové ploše jedním kliknutím definujte počáteční bod řádku a potom klikněte na tlačítko a táhnutím ukazatele k vytvoření požadovaného křivky.  
  
 Pokud chcete zavřít cestu, klikněte na první bod na řádku.  
  
### <a name="change-the-shape-of-a-curve"></a>Změna tvaru křivky  
 Použití **přímý výběr** nástroj ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362").  
  
 Klikněte na tvar a přetáhněte libovolného bodu na tvar, který má změnit křivky.  
  
### <a name="draw-a-free-form-path"></a>Nakreslení cesty volného tvaru  
 Použití **tužky** nástroj ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd").  
  
 Na návrhové ploše nakreslení cesty volného tvaru, stejně jako při použití skutečné tužky.  
  
### <a name="remove-part-of-a-path"></a>Odstranění části cesty  
 Použití **přímý výběr** nástroj ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362").  
  
 Vyberte cestu, která obsahuje segment, který chcete odstranit a potom klikněte na tlačítko **odstranit** tlačítko.  
  
### <a name="remove-a-point-in-a-path"></a>Odebrání bodu cestě  
 Použití **výběr** nástroj ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")a **pera** nástroj ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Použití **výběr** nástroj ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") vyberte cestu. Potom použijte **pera** nástroj ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") kliknout na bod, který chcete odebrat.  
  
### <a name="add-a-point-to-a-path"></a>Přidat bod na cestu  
 Použití **výběr** nástroj ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")a **pera** nástroj ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Použití **výběr** nástroj ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") vyberte cestu. Použití **pera** nástroj ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") k klikněte na libovolné místo v cestě, kam chcete přidat bod.  
  
##  <a name="Convert"></a> Převod tvaru na cestu  
 Pokud chcete změnit tvar stejným způsobem, že změníte cestu, převod tvaru na cestu.  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [práci s cestami: převod tvaru na cestu](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).  
  
##  <a name="Combine"></a> Spojit cesty  
 Cesty a tvary můžete zkombinovat do jedné cesty.  
  
 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-A338-4ef4-96c5-dae51cc1ca8a")  
  
|||||  
|-|-|-|-|  
|![](../designers/media/b1-1.png "B1_1")|Dva tvary před kombinování|![](../designers/media/b1-4.png "B1_4")|Intersect|  
|![](../designers/media/b1-2.png "B1_2")|Sjednocení|![](../designers/media/b1-5.png "B1_5")|Vyloučit překryv|  
|![](../designers/media/b1-3.png "B1_3")|Dělení|![](../designers/media/b1-6.png "B1_6")|Odečíst|  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [práci s cestami: Kombinovat cesty](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).  
  
##  <a name="Compound"></a> Vytvořit složenou cestu  
 Při vytváření složené cesty protínající části cesty jsou odečtena od výsledku a výslednou cestu převezme visual vlastnosti nejspodnějších cesty.  
  
 Můžete přerušit od sebe složené cesty kdykoli po jeho vytvoření.  
  
 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8DE5-b10d28f08a84")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [práci s cestami: vytvořit složenou cestu](https://www.youtube.com/watch?v=Io5bC0-nH6Q).  
  
##  <a name="Clipping"></a> Vytvořit ořezovou cestu  
 Ořezové cesty je cesta nebo tvar, který se použije na jiný objekt skrytí částí maskované objektu, které spadají mimo ořezové cesty.  
  
 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-A841-4f39-a3ef-36090cf5a625")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [práci s cestami: Vytvořit ořezovou cestu](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)



