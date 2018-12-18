---
title: Úpravy stylu objektů v Blendu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 70bf451a828e3884a6004f6304b91351e866ee52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843638"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Úpravy stylu objektů v Blendu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejjednodušší způsob, jak přizpůsobit objektu je můžete nastavit vlastnosti **vlastnosti** podokně.  
  
 Pokud chcete znovu použít nastavení nebo skupiny nastavení, vytvoření opakovaně použitelné prostředku. Může se jednat *styl*, *šablony*, nebo je příčina prostá, jako jsou vlastní barvy. Můžete provést také ovládací prvek zobrazí odlišně v závislosti na jeho stavu. Například tlačítko se změní na zelenou když na něj uživatel klikne.  
  
 **V tomto tématu**:  
  
-   [Štětce: Upravení vzhledu objektu](#Brushes)  
  
-   [Styly a šablony: vytvoření konzistentního vzhledu a chování napříč ovládacích prvků](#Styles)  
  
-   [Vizuální stavy: Změna vzhledu ovládacího prvku na základě stavu](#Visual)  
  
-   [Prostředky: Vytvoření barvy, styly a šablony a pozdější použití](#Resources)  
  
##  <a name="Brushes"></a> Štětce: Upravení vzhledu objektu  
 Použití štětce k objektu, pokud chcete změnit její vzhled.  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Editor štětců](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malování s opakováním image nebo vzor pro objekt  
 Vykreslení s použitím image nebo vzor pro objekt s opakováním *dlaždicového štětce*.  
  
 K vytvoření dlaždicového štětce, začněte vytvořením *obrázku štětce*, *kreslicí štětec*, nebo *vizuální štětec* prostředků.  
  
 Vytvoření obrázkový štětec pomocí obrázku. Na následujících obrázcích obrázkový štětec, obrázkový štětec vedle sebe a obrázkový štětec obráceně.  
  
 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png " 38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")  
  
 Vytvořením kreslicího štětce vektorové kreslení například cestu nebo tvar. Na následujících obrázcích kreslicího štětce, kreslicího štětce vedle sebe a kreslicího štětce obráceně.  
  
 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png " 15bf6021-620c-4490-9eae-086153d3f14f")  
  
 Vytvoření vizuální štětec pomocí ovládacího prvku, jako je například tlačítko. Na následujících obrázcích je vizuální štětec a vizuální štětec vedle sebe.  
  
 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [dlaždice štětce](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a> Styly a šablony: vytvoření konzistentního vzhledu a chování napříč ovládacích prvků  
 Můžete navrhnout vzhled a chování ovládacího prvku jednou a použití tohoto návrhu pro ostatní ovládací prvky, takže není nutné udržovat je jednotlivě.  
  
 **Byste měli použít styl?** : Pokud chcete nastavit výchozí vlastnosti (například barva tlačítka), použijte *styl*. Ovládací prvek můžete upravit, i když jste použili k němu stylu.  
  
 **Můžete použít šablonu?** : Pokud chcete změnit strukturu ovládacího prvku, použijte *šablony*. Představte si převod obrázek nebo logo na tlačítku. Ovládací prvek nelze změnit poté, co jste použili šablony do něj.  
  
### <a name="create-a-template-or-style"></a>Vytvořit šablonu nebo styl  
 Není k dispozici dva způsoby, jak vytvořit šablonu. Libovolný objekt lze převést na kreslicí ploše do ovládacího prvku nebo vytváříte šablonu na existující ovládací prvek.  
  
 Libovolný objekt převést na šablonu ovládacího prvku, vyberte objekt a pak na **nástroje** nabídce zvolte **Ujistěte se, do ovládacího prvku**.  
  
 Pokud chcete založit šablony na existující ovládací prvek, vyberte objekt na návrhové ploše. Potom v horní části návrhové plochy, klikněte na tlačítko s popisem cesty, zvolte **upravit šablonu**a klikněte na tlačítko **upravit kopii** nebo **vytvořit prázdnou**.  
  
 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")  
  
 Chcete-li vytvořit styl, vyberte objekt a potom v **objekt** nabídce zvolte **upravit styl**a klikněte na tlačítko **upravit kopii** nebo **vytvořit prázdnou**.  
  
- Zvolte **upravit kopii** začínat výchozí styl nebo šablonu ovládacího prvku.  
  
- Zvolte **vytvořit prázdnou** od záčátku.  
  
  **Upravit aktuální** možnost bude nabídnuta jen v případě, že upravit styl nebo šablonu, kterou jste vytvořili. Nebude se zobrazovat pro ovládací prvek, který je stále používá výchozí šablonu systému.  
  
  V **vytvořit prostředek stylu** dialogové okno, můžete buď pojmenovat stylu nebo šablony tak, aby ji mohli použít později, nebo použít styl nebo šablonu pro všechny ovládací prvky tohoto typu.  
  
  ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")  
  
> [!NOTE]
>  Nelze vytvořit styly a šablony pro každý typ ovládacího prvku. Pokud je nepodporuje ovládací prvek, tlačítko s popisem cesty nezobrazí výše na návrhovou plochu.  
>   
>  Chcete-li vrátit do rozsahu úprav hlavního dokumentu, klikněte na tlačítko **vrátit rozsah do** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b").  
>   
>  ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [vytvoření stylu](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [vytváření šablony ovládacího prvku v aplikaci Expression Blend](http://msdn.microsoft.com/expression/cc263912.aspx).  
  
### <a name="apply-a-style-or-template-to-a-control"></a>Platí pro ovládací prvek stylu nebo šablony  
 Klikněte pravým tlačítkem na objekt [objekty a časová osa](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelu, vyberte **upravit šablonu**a klikněte na tlačítko **aplikovat zdroj**.  
  
 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")  
  
### <a name="restore-the-default-style-or-template-of-a-control"></a>Obnovit výchozí styl nebo šablonu ovládacího prvku  
 Vyberte ovládací prvek a [vlastnosti](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelu, vyhledejte **styl** nebo **šablony** vlastnost. Potom klikněte na **pokročilé možnosti** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb")a potom klikněte na tlačítko **resetování** v místní nabídce.  
  
##  <a name="Visual"></a> Vizuální stavy: Změna vzhledu ovládacího prvku na základě stavu  
 Ovládací prvky mohou mít různé vizuální vzhled na základě interakcí uživatele. Například můžete provést na tlačítko se změní na zelenou když na něj uživatel klikne nebo můžete spustit animaci. Zkraťte nebo prodloužit doba mezi vizuálních stavů pomocí přechodů.  
  
 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Správa stavu ovládacích prvků WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a> Prostředky: Vytvoření barvy, styly a šablony a pozdější použití  
 Můžete převést prakticky cokoliv ve vašem projektu a prostředek. Prostředek je právě objekt, který můžete ve své aplikaci využít v různých místech. Můžete například vytvořit jednou barvu, usnadňují prostředek a potom použít na několik objektů. Chcete-li změnit barvu všech těchto objektů, stačí změňte barvu prostředků.  
  
 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-B153-52a23cd744f7") ![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [stručný dotykové ovládání s prostředky](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)



