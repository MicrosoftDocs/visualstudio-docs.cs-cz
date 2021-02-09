---
title: Zakázat povědomí o DPI v aplikaci Visual Studio
description: Popisuje omezení Návrhář formulářů na monitorování HDPI a postup spuštění sady Visual Studio jako procesu nepodporujícího DPI.
ms.date: 09/28/2020
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.topic: conceptual
ms.openlocfilehash: f63d831127951815f28955e72ae29b1a4d7f5a3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917097"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Zakázat povědomí o DPI v aplikaci Visual Studio

Visual Studio je aplikace podporující tečky na palec (DPI), což znamená, že se displej škáluje automaticky. Pokud aplikace uvádí, že se nejedná o rozlišení DPI, operační systém aplikaci škáluje jako rastrový obrázek. Toto chování se také označuje jako virtualizace DPI. Aplikace stále popřemýšleje o tom, že je spuštěná v 100% škálování nebo 96 dpi.

Tento článek pojednává o omezeních Návrhář formulářů v monitorování HDPI a o tom, jak spustit sadu Visual Studio jako proces nepodporující DPI.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Návrhář formulářů v monitorování HDPI

**Návrhář formulářů** v aplikaci Visual Studio nemá podporu škálování. To způsobuje problémy při otevření některých formulářů v **Návrhář formulářů** na monitorech s vysokými tečkami na palec (HDPI). Například ovládací prvky se mohou překrývat, jak je znázorněno na následujícím obrázku:

![Návrhář formulářů na monitoru HDPI](./media/win-forms-designer-hdpi.png)

Když otevřete formulář v **Návrhář formulářů** v aplikaci Visual Studio na monitoru HDPI, Visual Studio zobrazí žlutý informační panel v horní části návrháře:

![Informační panel v aplikaci Visual Studio pro restartování v režimu nezohledňující rozlišení DPI](./media/scaling-gold-bar.png)

U zprávy se **ve vašem hlavním zobrazení načtou změny, které jsou nastavené na 200% (192 DPI). To může způsobit problémy s vykreslováním v okně návrháře.**

> [!NOTE]
> Tento informační panel byl představen v aplikaci Visual Studio 2017 verze 15,8.

Pokud v Návrháři nepracujete a nepotřebujete upravovat rozložení formuláře, můžete informační panel ignorovat a pokračovat v práci v editoru kódu nebo v jiných typech návrháře. (Můžete také [zakázat oznámení](#disable-notifications) , aby se informační panel nadále nezobrazoval.) Je ovlivněna pouze **Návrhář formulářů** . Pokud potřebujete pracovat v **Návrhář formulářů**, další část vám pomůže tento [problém vyřešit](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Řešení problému se zobrazením

Existují tři možnosti, jak vyřešit problém se zobrazením:

- [Restartování sady Visual Studio jako procesu nepodporujícího DPI](#restart-visual-studio-as-a-dpi-unaware-process)
- [Přidat položku registru](#add-a-registry-entry)
- [Nastavte nastavení škálování zobrazení na 100%.](#set-your-display-scaling-setting-to-100)

> [!TIP]
> Pokud upřednostňujete správu nastavení z příkazového řádku, [`devenv.exe`](../ide/reference/devenv-command-line-switches.md) přebírá `/noscale` jako parametr příkazového řádku, který se má spustit v režimu škálování 100%.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Restartování sady Visual Studio jako procesu nepodporujícího DPI

Aplikaci Visual Studio můžete restartovat jako proces nepodporující DPI tím, že vyberete možnost na žlutém informačním panelu. Toto je preferovaný způsob řešení problému.

Pokud je aplikace Visual Studio spuštěna jako proces nezohledňující rozlišení DPI, jsou vyřešeny problémy rozložení návrháře, ale písma mohou být rozmazaný. Visual Studio zobrazí jinou žlutou informační zprávu, když běží jako proces nepodporující DPI, který říká, že **Visual Studio běží jako proces nepodporující dpi. Návrháři WPF a XAML se nemusí zobrazit správně.** Informační panel také nabízí možnost **restartovat aplikaci Visual Studio jako proces podporující dpi**.

> [!NOTE]
> - Pokud jste v aplikaci Visual Studio v systému Windows neukotveni okna nástrojů, když jste vybrali možnost restartování jako proces, který nepracuje s rozlišením DPI, může se poloha těchto oken nástroje změnit.
> - Použijete-li výchozí profil Visual Basic, nebo pokud máte v **nabídce nástroje** možnosti projektů a řešení možnost **Uložit nové projekty**  >    >  , aplikace Visual Studio nemůže projekt znovu otevřít, když se restartuje jako proces nezohledňující rozlišení DPI. Projekt ale můžete otevřít tak, že ho vyberete v části **soubor**  >  **Poslední projekty a řešení**.

Po dokončení práce na **Návrhář formulářů** je důležité restartovat aplikaci Visual Studio jako proces podporující dpi. Když je spuštěný jako proces nezohledňující rozlišení DPI, můžou písma vypadat rozmazaně a můžou se zobrazit problémy v jiných návrhářích, jako je **Návrhář XAML**. Pokud aplikaci Visual Studio zavřete a znovu otevřete, když je spuštěná v režimu nezohledňující rozlišení DPI, bude se znovu používat DPI. Můžete také vybrat možnost **restartovat Visual Studio jako možnost procesu podporujícího rozlišení DPI** na informačním panelu.

### <a name="add-a-registry-entry"></a>Přidat položku registru

Aplikaci Visual Studio můžete označit jako nezohledňované DPI úpravou registru. Otevřete **Editor registru** a přidejte položku do podklíče **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** :

**Položka**: v závislosti na tom, zda používáte sadu Visual Studio 2017 nebo 2019, použijte jednu z těchto hodnot:

- C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Pokud používáte edici Professional nebo Enterprise sady Visual Studio, nahraďte v záznamu **komunitou** **Professional** nebo **Enterprise** . Písmeno jednotky také nahraďte podle potřeby.

**Zadejte**: REG_SZ

**Hodnota**: DPIUNAWARE

> [!NOTE]
> Visual Studio zůstane v režimu nepodporujícím DPI, dokud neodeberete položku registru.

### <a name="set-your-display-scaling-setting-to-100"></a>Nastavte nastavení škálování zobrazení na 100%.

Pokud chcete nastavit nastavení škálování pro zobrazení na 100% ve Windows 10, zadejte do vyhledávacího pole na hlavním panelu možnost **Nastavení zobrazení** a pak vyberte **změnit nastavení zobrazení**. V okně **Nastavení** nastavte **změnit velikost textu, aplikací a dalších položek** na **100%**.

Nastavení škálování zobrazení na 100% může být nežádoucí, protože může způsobit, že uživatelské rozhraní je pro použití příliš malé.

## <a name="disable-notifications"></a>Zakázat oznámení

V aplikaci Visual Studio se můžete rozhodnout, že nebudete upozorňováni na problémy s škálováním DPI. Pokud v Návrháři nepracujete, možná budete chtít zakázat oznámení, například.

Chcete-li zakázat oznámení , klikněte na tlačítko  >  **Možnosti** nástrojů a otevřete dialogové okno **Možnosti** . Pak zvolte **Návrhář formulářů**  >  **Obecné** a nastavte **oznámení škálování dpi** na **false**.

![Možnost oznámení škálování DPI v aplikaci Visual Studio](./media/notifications-option.png)

Pokud chcete později znovu povolit oznámení o škálování, nastavte vlastnost na **hodnotu true**.

## <a name="troubleshoot"></a>Řešení potíží

Pokud převod na základě rozlišení DPI v aplikaci Visual Studio nefunguje podle očekávání, zkontrolujte, zda je v `dpiAwareness` Editoru registru v podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** uvedena hodnota. Pokud je tato hodnota přítomná, odstraňte ji.

## <a name="see-also"></a>Viz také

- [Automatické škálování v model Windows Forms](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
