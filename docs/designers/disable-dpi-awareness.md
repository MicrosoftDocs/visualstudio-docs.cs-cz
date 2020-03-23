---
title: Zakázání povědomí o DPI v sadě Visual Studio
description: Popisuje omezení Windows Forms Designer na monitorech HDPI a jak spustit Visual Studio jako proces dpi nevědomý.
ms.date: 04/05/2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: 8e7a5a5871b66fd388d7c5a9f774a22163d06729
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589562"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Zakázání povědomí o DPI v sadě Visual Studio

Visual Studio je aplikace podporující palce (DPI), což znamená, že zobrazení se automaticky škáluje. Pokud aplikace uvádí, že není podporující DPI, operační systém škáluje aplikace jako bitmap. Toto chování se také nazývá virtualizace DPI. Aplikace si stále myslí, že je spuštěna na 100% škálování nebo 96 dpi.

Tento článek popisuje omezení Windows Forms Designer na monitorech HDPI a jak spustit Visual Studio jako proces dpi nevědomý.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Návrhář formulářů Windows na monitorech HDPI

**Návrhář formulářů Windows v** sadě Visual Studio nemá podporu škálování. To způsobí problémy se zobrazením při otevření některých formulářů v **Návrháři formulářů systému Windows** na monitorech s vysokými tečkami na palec (HDPI). Například ovládací prvky se mohou překrývat, jak je znázorněno na následujícím obrázku:

![Návrhář formulářů Windows na monitoru HDPI](./media/win-forms-designer-hdpi.png)

Když otevřete formulář v **Návrháři formulářů Windows** v sadě Visual Studio na monitoru HDPI, Visual Studio zobrazí žlutý informační pruh v horní části návrháře:

![Informační panel v sadě Visual Studio restartování v režimu dpi nevědomý](./media/scaling-gold-bar.png)

Zpráva čte **škálování na hlavním displeji je nastavena na 200 % (192 dpi). To může způsobit problémy s vykreslováním v okně návrháře.**

> [!NOTE]
> Tento informační panel byl představen ve Visual Studiu 2017 verze 15.8.

Pokud v návrháři nepracujete a nepotřebujete upravit rozložení formuláře, můžete informační panel ignorovat a pokračovat v práci v editoru kódu nebo v jiných typech návrhářů. (Oznámení můžete také [zakázat,](#disable-notifications) aby se informační pruh nezobrazoval.) Ovlivněna je pouze **aplikace Windows Forms Designer.** Pokud potřebujete pracovat v **Návrháři formulářů systému Windows**, další část vám pomůže [problém vyřešit](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Vyřešení problému se zobrazením

Problém se zobrazením lze vyřešit třemi možnostmi:

- [Restartujte Visual Studio jako proces, který nepředpokládá dpi](#restart-visual-studio-as-a-dpi-unaware-process)
- [Přidání položky registru](#add-a-registry-entry)
- [Nastavení měřítka displeje na 100 %](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Restartujte Visual Studio jako proces, který nepředpokládá dpi

Aplikaci Visual Studio můžete restartovat jako proces, který nepředpokládá dpi, výběrem možnosti na žlutém informačním panelu. Toto je upřednostňovaný způsob řešení problému.

Při spuštění sady Visual Studio jako proces dpi nevědomý, problémy s rozložením návrháře jsou vyřešeny, ale písma se může zobrazit rozmazaný. Visual Studio zobrazí jinou žlutou informační zprávu, když běží jako proces dpi nevědomý, který říká, že **Visual Studio běží jako proces dpi nevědomý. Návrháři WPF a XAML se nemusí zobrazit správně.** Informační panel také poskytuje možnost **restartovat visual studio jako proces podporující DPI**.

> [!NOTE]
> - Pokud jste měli undocked okna nástrojů v sadě Visual Studio při výběru možnost restartovat jako proces dpi nevědomý, umístění těchto oken nástrojů může změnit.
> - Pokud použijete výchozí profil jazyka Visual Basic nebo pokud máte možnost **Uložit nové projekty při vytvoření** nevybranou v části**Projekty a řešení****možnosti** >  **nástroje** > , visual studio nemůže znovu otevřít projekt při restartování jako proces dpi nevědomý. Projekt však můžete otevřít tak, že jej vyberete v části **Soubor** > **posledních projektů a řešení**.

Po dokončení práce v **Návrháři formulářů systému Windows**je důležité restartovat aplikaci Visual Studio jako proces podporující dpi. Když je spuštěn jako proces dpi nevědomý, písma mohou vypadat rozmazaně a může se zobrazit problémy v jiných návrhářů, jako je **například Návrhář XAML**. Pokud zavřete a znovu otevřete Visual Studio, když je spuštěnv režimu dpi nevědomý, stane dpi znovu. Můžete také klepnout na **možnost Restartovat visual studio jako** proces podporující DPI na informačním panelu.

### <a name="add-a-registry-entry"></a>Přidání položky registru

Úpravou registru můžete označit aplikaci Visual Studio jako dpi, která nepředpokládá. Otevřete **Editor registru** a přidejte položku do **podklíče HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers:**

**Položka**: V závislosti na tom, jestli používáte Visual Studio 2017 nebo 2019, použijte jednu z těchto hodnot:

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Pokud používáte edici Professional nebo Enterprise v sadě Visual Studio, nahraďte **komunitu** v položce **profesionálem** nebo **podnikem.** Podle potřeby také vyměňte písmeno jednotky.

**Typ**: REG_SZ

**Hodnota**: DPIUNAWARE

> [!NOTE]
> Visual Studio zůstane v režimu DPI nevědomý, dokud odebrat položku registru.

### <a name="set-your-display-scaling-setting-to-100"></a>Nastavení měřítka displeje na 100 %

Pokud chcete nastavení měřítka zobrazení nastavit na 100 % ve Windows 10, zadejte **nastavení zobrazení** do vyhledávacího pole na hlavním panelu a pak vyberte Změnit **nastavení zobrazení**. V okně **Nastavení** nastavte **Možnost Změnit velikost textu, aplikací a dalších položek** na **100 %**.

Nastavení měřítka displeje na 100 % může být nežádoucí, protože může způsobit, že uživatelské rozhraní bude příliš malé, aby bylo použitelné.

## <a name="disable-notifications"></a>Zakázání oznámení

Můžete se rozhodnout, že nebudete upozorňováni na problémy s škálováním DPI v sadě Visual Studio. Oznámení můžete zakázat, například pokud nepracujete v návrháři.

Chcete-li zakázat oznámení, zvolte**Možnosti** **nástrojů** > a otevřete dialogové okno **Možnosti.** Potom zvolte **Windows Forms Designer** > **General**a nastavte **oznámení měřítka DPI** na **false**.

![Možnost oznámení o změně měřítka DPI v sadě Visual Studio](./media/notifications-option.png)

Pokud chcete později znovu povolit oznámení škálování, nastavte vlastnost **true**.

## <a name="troubleshoot"></a>Řešení potíží

Pokud přechod povědomí o dpi nefunguje podle očekávání v sadě Visual `dpiAwareness` Studio, zkontrolujte, zda máte hodnotu v **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Možnosti spuštění souboru image\devenv.exe** v Editoru registru. Odstraňte hodnotu, pokud je k dispozici.

## <a name="see-also"></a>Viz také

- [Automatické škálování ve Formulářích systému Windows](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
