---
title: Animace objektů v Návrhář XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ea2fdf1f47385a9be26fa65a93b9104b2d864079
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658026"
---
# <a name="animate-objects-in-xaml-designer"></a>Animace objektů v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit krátké animace, které přesouvají objekty, nebo je Zeslabit.

 Začněte tím, že vytvoříte *scénář*. Scénář obsahuje jednu nebo více *časových os*. Nastavte *klíčové snímky* na časové ose, aby bylo možné označit změny vlastností. Poté při spuštění animace Blend interpoluje změny vlastností během stanoveného časového období. Výsledkem je hladký přechod. Můžete animovat jakoukoli vlastnost, která patří objektu, i nevizuální vlastnosti.

 Následující ilustrace znázorňuje scénář nazvaný **nahoru**. Časová osa obsahuje klíčové snímky, které označují polohu X a Y obdélníku. Když se tato animace spustí, obdélník se přesune z jedné pozice do druhé plynule.

 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")

 Naučte se vytvářet animace pomocí sledování těchto videí.

|Podívejte se na krátké video:|Přečtěte si, jak:|
|--------------------------|-------------------|
|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Vytvoření časových os](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Vytvořte časovou osu a pracujte s objekty na časové ose.|
|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Přidání klíčových snímků a opakování animace](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Přidejte klíčové snímky a nastavte vlastnosti u každého klíčového snímku. Potom spusťte animaci a sledujte objekty plynule přechod mezi nimi.|
|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Přidání aktivačních událostí pro interaktivitu](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Spustí animaci, když dojde k události. Například začněte při načtení okna.|
|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [animace barev](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|K změně barvy objektu použijte animaci.|
|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [vytváření a úpravy cest pohybu](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animovat objekty podél cesty.|
|![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [usnadňuje klíčové snímky](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Urychlení nebo zpomalení animace poblíž začátku (*náběh/s* *) nebo*blízko konce animace|
|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [animace tlačítka](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Vytvoří zajímavé efekty, které se zobrazí na tlačítku, když na něj uživatel odkazuje.|
|![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Vytvoření animace a práce s náběh a doběh](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Animace efektů, které se zobrazí, když uživatel stiskne tlačítko myši na obrázku kalkulačky.|

## <a name="see-also"></a>Viz také
 [Vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
