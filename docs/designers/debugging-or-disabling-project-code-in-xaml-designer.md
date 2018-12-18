---
title: Ladění nebo zakázání kódu projektu v Návrháři XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 191d180a68edd439c729fa963b607c992ff3c00e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816775"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>Ladění nebo zakázání kódu projektu v Návrháři XAML

V mnoha případech neošetřené výjimky v **XAML** Návrhář může být způsobeno kód projektu pokusu o přístup k vlastnosti nebo metody, které vracet různé hodnoty, nebo fungují jiným způsobem, při spuštění aplikace v návrháři. Můžete tyto výjimky vyřešit ladění kódu projektu v jiné instanci sady Visual Studio nebo dočasně zakázat kód projektu v Návrháři tak zabránit výjimky.

Kód projektu zahrnuje:

-   Vlastní ovládací prvky a uživatelských ovládacích prvků

-   Knihovny tříd

-   Převodníky hodnot

-   Vazby proti návrhovém generován z kódu projektu

Když kód projektu je zakázaný, sada Visual Studio zobrazí zástupné symboly. Například sada Visual Studio zobrazí název vlastnosti pro vazbu, kde data už nejsou k dispozici, nebo zástupný symbol pro ovládací prvek, který je již neběží.

![Dialogové okno neošetřené výjimky](../designers/media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Chcete-li zjistit, zda kód projektu je příčinou výjimku

1.  V dialogovém okně neošetřenou výjimku, zvolte **klinutím sem zopakujete zavedení návrháře** odkaz.

2.  Na panelu nabídek zvolte **ladění** > **spustit ladění** sestavíte a spustíte aplikaci.

     Pokud se aplikace sestaví a spustí úspěšně, výjimka návrhu může být způsobeno spuštění v Návrháři projektu kódu.

## <a name="to-debug-project-code-running-in-the-designer"></a>Chcete-li ladit projekt kódu spuštěného v Návrháři

1.  V dialogovém okně neošetřenou výjimku, zvolte **kliknutím sem zakážete spuštění kódu projektu a opětovné načtení návrháře** odkaz.

2.  Vyberte ve Správci úloh Windows **ukončit úlohu** zavřete všechny instance návrháři XAML sady Visual Studio, které jsou aktuálně spuštěny.

     ![Instance návrháře XAML v Správce úloh](../designers/media/xaml_taskmanager.png)

3.  V sadě Visual Studio otevřete stránku XAML, který bude obsahovat kód nebo ovládací prvek, který chcete ladit.

4.  Otevřete novou instanci sady Visual Studio a pak otevřete druhou instanci projektu.

5.  Nastavte zarážku v kódu projektu.

6.  V nové instanci sady Visual Studio na řádku nabídek zvolte **ladění** > **připojit k procesu**.

7.  V **připojit k procesu** dialogového okna v **procesy k dispozici** klikněte na položku **XDesProc.exe**a klikněte na tlačítko **připojit** tlačítko.

     ![Proces návrháře XAML](../designers/media/xaml_attach.png)

     Jedná se o proces pro návrháře XAML v první instance sady Visual Studio.

8.  V první instanci sady Visual Studio na panelu nabídek zvolte **ladění** > **spustit ladění**.

     Nyní můžete krokovat do svého kódu, který je spuštěn v návrháři.

## <a name="to-disable-project-code-in-the-designer"></a>Chcete-li zakázat kód projektu v Návrháři

-   V dialogovém okně neošetřenou výjimku, zvolte **kliknutím sem zakážete spuštění kódu projektu a opětovné načtení návrháře** odkaz.

-   Taky můžete na panelu nástrojů **návrháře XAML**, zvolte **zakázat kód projektu** tlačítko.

     ![Tlačítko Zakázat kód projektu](../designers/media/xaml_disablecode.png)

     Můžete přepínat na tlačítko znovu pro opětovné povolení kódu projektu.

    > [!NOTE]
    > Pro projekty, které cílí ARM nebo X64 procesory, Visual Studio nelze spustit kód projektu v návrháři, proto **zakázat kód projektu** je tlačítko neaktivní v návrháři.

-   Možnost způsobí, že návrháře znovu načíst a potom zakázat veškerý kód pro přidružený projekt.

    > [!NOTE]
    > Zakázání kódu projektu může vést ke ztrátám dat doby návrhu. Alternativou je pro ladění kódu spuštěného v návrháři.

## <a name="control-display-options"></a>Možnosti zobrazení ovládacího prvku

> [!NOTE]
> **Možnosti zobrazení ovládání** je dostupná jenom pro aplikace univerzální platformy Windows, které se zaměřují Windows 10 Fall Creators Update (sestavení 16299) nebo novější. **Možnosti zobrazení ovládacího prvku** funkce je k dispozici v sadě Visual Studio 2017 verze 15.9 nebo vyšší. 

V Návrháři XAML můžete změnit možnosti zobrazení ovládacího prvku můžete zobrazit jenom ovládacích prvků platformy ze sady Windows SDK. Toto může vylepšit spolehlivost tohoto návrháře XAML.

Chcete-li změnit možnosti zobrazení ovládacího prvku, klikněte na ikonu v levé dolní části okna návrháře a potom vyberte možnosti v části **možnosti zobrazení ovládacího prvku**:

![Možnosti zobrazení ovládacího prvku](../designers/media/control_display_options.png)

Když vyberete **pouze ovládací prvky zobrazení platformy**, všechny vlastní ovládací prvky pocházející ze sad SDK, zákazníka uživatelské ovládací prvky a další, se nevykreslí úplně. Místo toho budou nahrazeny náhradní ovládací prvky k předvedení velikost a umístění ovládacího prvku.

## <a name="see-also"></a>Viz také:

- [Návrh XAML v sadě Visual Studio a nástroje Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)
