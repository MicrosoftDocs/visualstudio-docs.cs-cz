---
title: Ladění nebo zakázání kódu projektu v Návrháři XAML
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: fba240c29cb8142a9ec4b4d28c71112c1974a5b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331064"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>Ladění nebo zakázání kódu projektu v Návrháři XAML

V mnoha případech může být Neošetřená výjimka v Návrhář XAML způsobena tím, že kód projektu se pokusí získat přístup k vlastnostem nebo metodám, které vracejí jiné hodnoty, nebo pracovat jiným způsobem, pokud vaše aplikace běží v návrháři. Tyto výjimky můžete vyřešit laděním kódu projektu v jiné instanci sady Visual Studio nebo dočasně zabránit výjimkám zakázáním kódu projektu v návrháři.

Kód projektu zahrnuje:

- Vlastní ovládací prvky a uživatelské ovládací prvky

- Knihovny tříd

- Převaděče hodnot

- Vazby na data doby návrhu generovaná z kódu projektu

Když je kód projektu zakázán, Visual Studio zobrazí zástupné symboly. Například Visual Studio zobrazuje název vlastnosti pro vazbu, kde data již nejsou k dispozici, nebo zástupný symbol pro ovládací prvek, který již není spuštěn.

![Neošetřená výjimka – dialogové okno](media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Určení, zda kód projektu způsobuje výjimku

1. V dialogu Neošetřená výjimka vyberte **kliknutím sem znovu načtěte odkaz návrháře** .

2. Na panelu nabídek vyberte **ladit**  >  **Spustit ladění** a sestavte a spusťte aplikaci.

     V případě úspěšného sestavení a spuštění aplikace může být výjimka v době návrhu způsobena kódem vašeho projektu spuštěným v návrháři.

## <a name="to-debug-project-code-running-in-the-designer"></a>Ladění kódu projektu spuštěného v Návrháři

1. V dialogu Neošetřená výjimka vyberte **kliknutím sem zakážete spuštění kódu projektu a znovu načtěte odkaz návrháře** .

2. Ve Správci úloh systému Windows klikněte na tlačítko **Ukončit úlohu** a zavřete tak všechny instance Návrhář XAML sady Visual Studio, které jsou aktuálně spuštěny.

     ![Instance návrháře XAML v TaskManager](media/xaml_taskmanager.png)

3. V aplikaci Visual Studio otevřete stránku XAML, která obsahuje kód nebo ovládací prvek, který chcete ladit.

4. Otevřete novou instanci sady Visual Studio a poté otevřete druhou instanci projektu.

5. Nastavte zarážku v kódu projektu.

6. V nové instanci aplikace Visual Studio, na panelu nabídek vyberte možnost **ladit**  >  **připojení k procesu**.

7. V dialogovém okně **připojit k procesu** vyberte v seznamu **procesy k dispozici** možnost **XDesProc.exe**a pak klikněte na tlačítko **připojit** .

     ![Proces návrháře XAML](media/xaml_attach.png)

     To je proces pro návrháře XAML v první instanci sady Visual Studio.

8. V první instanci sady Visual Studio, na panelu nabídek vyberte **ladit**  >  **Spustit ladění**.

     Nyní můžete krokovat kód, který je spuštěn v návrháři.

## <a name="to-disable-project-code-in-the-designer"></a>Zakázání kódu projektu v Návrháři

- V dialogu Neošetřená výjimka vyberte **kliknutím sem zakážete spuštění kódu projektu a znovu načtěte odkaz návrháře** .

- Případně můžete na panelu nástrojů v **Návrháři XAML**zvolit tlačítko **Zakázat kód projektu** .

     ![Tlačítko Zakázat kód projektu](media/xaml_disablecode.png)

     Můžete znovu přepínat tlačítko a znovu povolit kód projektu.

    > [!NOTE]
    > Pro projekty, které cílí na procesory ARM nebo x64, nemůže Visual Studio spustit kód projektu v návrháři, takže tlačítko **Zakázat kód projektu** je v Návrháři zakázané.

- Kterákoli z možností způsobí, že Návrhář znovu načte a potom zakáže veškerý kód pro přidružený projekt.

    > [!NOTE]
    > Zakázání kódu projektu může vést ke ztrátě dat v době návrhu. Alternativou je ladění kódu spuštěného v návrháři.

## <a name="control-display-options"></a>Možnosti zobrazení ovládacího prvku

> [!NOTE]
> **Možnosti zobrazení ovládacích prvků** jsou dostupné jenom pro Univerzální platforma Windows aplikace, které cílí na Windows 10 na aktualizace Creators Update (Build 16299) nebo novější. Funkce **Možnosti zobrazení ovládacích prvků** je k dispozici v aplikaci Visual Studio 2017 verze 15,9 nebo novější.

V Návrháři XAML můžete změnit možnosti zobrazení ovládacího prvku tak, aby zobrazovaly pouze ovládací prvky platformy z Windows SDK. To může zlepšit spolehlivost návrháře XAML.

Chcete-li změnit možnosti zobrazení ovládacího prvku, klikněte na ikonu v levém dolním rohu okna návrháře a potom vyberte možnost v části **Možnosti zobrazení ovládacího prvku**:

![Možnosti zobrazení ovládacího prvku](media/control_display_options.png)

Když vyberete **pouze ovládací prvky zobrazení platformy**, všechny vlastní ovládací prvky přicházející ze sady SDK, uživatelské ovládací prvky zákazníka a další nebudou vykresleny úplně. Místo toho jsou nahrazeni záložními ovládacími prvky, aby ukázaly velikost a polohu ovládacího prvku.

## <a name="see-also"></a>Viz také

- [Návrh XAML v aplikaci Visual Studio a Blend pro Visual Studio](designing-xaml-in-visual-studio.md)
