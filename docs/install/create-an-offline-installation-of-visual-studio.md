---
title: Vytvoření offline instalace
description: Zjistěte, jak nainstalovat Visual Studio offline, pokud máte nespolehlivé připojení k internetu nebo nízkou šířku pásma.
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b10fc1adbb0b4a6e053549749ea90acf3919d0c6
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602201"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Vytvoření offline instalace sady Visual Studio

::: moniker range="vs-2017"

Navrhli jsme Visual Studio 2017, aby dobře fungoval v různých konfiguracích sítě a počítače. Přestože doporučujeme vyzkoušet si webový instalační program [Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads)což je malý soubor, který vám umožní mít aktuální informace o všech nejnovějších opravách a funkcích, o kterých víme, že to možná &mdash; nebudete moct &mdash; provést.

::: moniker-end

::: moniker range=">=vs-2019"

Navrhli jsme Visual Studio 2019 a novějších verzích tak, aby dobře fungovaly v různých konfiguracích sítí a počítačů. Přestože doporučujeme vyzkoušet si webový instalační program [Visual Studio,](https://visualstudio.microsoft.com/downloads)což je malý soubor, který vám umožní mít aktuální informace o všech nejnovějších opravách a funkcích, o kterých víme, že to možná &mdash; nebudete moct &mdash; provést.

::: moniker-end

Můžete mít například nespolehlivé připojení k internetu nebo připojení s nízkou šířkou pásma. Pokud ano, máte několik možností: Pomocí nové funkce "Stáhnout vše a pak nainstalovat" můžete stáhnout soubory před instalací nebo můžete pomocí příkazového řádku vytvořit místní mezipaměť souborů.

> [!NOTE]
> Pokud jste podnikový správce, který chce provést nasazení služby Visual Studio do sítě klientských pracovních stanic, které jsou brány firewall z internetu, podívejte se na naše stránky Vytvoření síťové instalace [Visual Studio](../install/create-a-network-installation-of-visual-studio.md) Visual Studio Instalace certifikátů požadovaných pro [offline](../install/install-certificates-for-visual-studio-offline.md) instalační stránky.

## <a name="use-the-download-all-then-install-feature"></a>Použijte funkci Stáhnout vše a pak nainstalovat.

::: moniker range="vs-2017"

[**Novinka ve verzi 15.8:**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install)Po stažení webového instalačního programu vyberte novou možnost Stáhnout vše a pak z nabídky Instalační program pro Visual Studio.  Pak pokračujte v instalaci.

   ![Možnost Stáhnout vše a pak nainstalovat](media/download-all-then-install.png)

::: moniker-end

::: moniker range=">=vs-2019"

Po stažení webového instalačního programu vyberte novou možnost **Stáhnout vše** a pak nainstalovat z Instalační program pro Visual Studio. Pak pokračujte v instalaci.

   ![Možnost Stáhnout vše a pak nainstalovat](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Navrhli jsme funkci Stáhnout vše, pak nainstalovat, abyste si Visual Studio mohli stáhnout jako jednu instalaci pro stejný počítač, na kterém jste ho stáhli. Tímto způsobem se můžete bezpečně odpojit od webu před instalací Visual Studio.

> [!IMPORTANT]
> K vytvoření offline mezipaměti, kterou chcete přenést do jiného počítače, nepoužívejte funkci Stáhnout vše, pak nainstalovat. Není navržená tak, aby takto fungovala. <br><br>Pokud chcete vytvořit offline mezipaměť na místním počítači, kterou pak můžete použít k instalaci Visual Studio, podívejte se na část Použití příkazového řádku k vytvoření [místní mezipaměti](#use-the-command-line-to-create-a-local-cache) níže.  Případně můžete na [stránce Vytvořit síťovou instalaci Visual Studio](../install/create-a-network-installation-of-visual-studio.md) informace o tom, jak vytvořit mezipaměť v síti.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Použití příkazového řádku k vytvoření místní mezipaměti
::: moniker range="vs-2017"

Po stažení malého bootstrapperu pomocí příkazového řádku vytvořte místní mezipaměť. Pak pomocí místní mezipaměti nainstalujte Visual Studio. (Tento proces nahrazuje soubory ISO, které byly k dispozici pro předchozí verze). 

::: moniker-end

::: moniker range=">=vs-2019"

Po stažení malého souboru bootstrapperu pomocí příkazového řádku vytvořte místní mezipaměť. Pak pomocí místní mezipaměti nainstalujte Visual Studio.

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 – stažení Visual Studio bootstrapperu

K dokončení tohoto kroku musíte mít připojení k internetu.

::: moniker range="vs-2017"

Pokud chcete získat nejnovější zaváděcí nástroj pro Visual Studio 2017 verze 15.9, přejděte na stránku Visual Studio předchozí verze [a](https://visualstudio.microsoft.com/vs/older-downloads/) stáhněte si jeden z následujících souborů bootstrapperu:

| Edice                                      | Název_souboru            |
|----------------------------------------------|---------------------|
| Visual Studio Professional 2017 verze 15.9 | vs_professional.exe |
| Visual Studio Enterprise 2017 verze 15.9   | vs_enterprise.exe   |
| Visual Studio Build Tools 2017 verze 15.9  | vs_buildtools.exe   |

::: moniker-end

::: moniker range="vs-2019"

Začněte tím, že si stáhnete zaváděcí nástroj Visual Studio 2019 ze stránky [Visual Studio ke](https://visualstudio.microsoft.com/downloads) stažení nebo ze stránky vydání [Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) pro zvolenou verzi a edici Visual Studio. Instalační soubor nebo zaváděcí nástroj se bude shodovat nebo bude podobný &mdash; &mdash; jednomu z následujících:

| Edice                         | Soubor                                                                                                                                                                                                                               |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio 2019 Build Tools  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
> Vydané verze Visual Studio 2022 ještě nejsou k dispozici, nástroje bootstrappers níže jsou pro verzi Preview Visual Studio 2022.
>Začněte stažením zaváděcího nástroje Visual Studio 2022 ze [stránky Visual Studio stahování.](https://aka.ms/vs2022preview)

| Edice                         | Stáhnout                                                            |
|---------------------------------|---------------------------------------------------------------------|
| Visual Studio 2022 Professional | [vs_professional.exe](https://aka.ms/vs/17/pre/vs_professional.exe) |
| Visual Studio 2022 Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/pre/vs_enterprise.exe)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Pokud jste si už dříve stáhli soubor bootstrapperu a chcete ověřit jeho verzi, tady je postup. Ve Windows otevřete Průzkumník souborů, klikněte pravým tlačítkem na soubor bootstrapperu, zvolte **Vlastnosti,** zvolte kartu Podrobnosti a zobrazte **číslo verze** produktu.  Pokud chcete toto číslo porovnat s verzí Visual Studio, přečtěte si Visual Studio [čísla sestavení](/visual-studio-build-numbers-and-release-dates.md) a data vydání.

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Pokud jste si předtím stáhli soubor bootstrapperu a chcete ověřit jeho verzi, tady je postup. Ve Windows otevřete Průzkumník souborů, klikněte pravým tlačítkem na soubor bootstrapperu, zvolte **Vlastnosti,** zvolte kartu Podrobnosti a zobrazte **číslo verze** produktu.  Pokud chcete toto číslo porovnat s verzí Visual Studio, podívejte se [na stránku Visual Studio verze 2019.](/visualstudio/releases/2019/history)

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Pokud jste si předtím stáhli soubor bootstrapperu a chcete ověřit jeho verzi, tady je postup. Ve Windows otevřete Průzkumník souborů, klikněte pravým tlačítkem na soubor bootstrapperu, zvolte **Vlastnosti,** zvolte kartu Podrobnosti a zobrazte **číslo verze** produktu.  Pokud chcete toto číslo porovnat s verzí Visual Studio, podívejte se na [stránku Visual Studio verze 2022.](/visualstudio/releases/2022/history)

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>Krok 2 – vytvoření místní instalační mezipaměti

K dokončení tohoto kroku musíte mít připojení k internetu.

Otevřete příkazový řádek a použijte parametry bootstrapperu, jak jsou definovány v části Použití parametrů příkazového řádku k instalaci [Visual Studio](use-command-line-parameters-to-install-visual-studio.md) k vytvoření místní instalační mezipaměti. Běžné příklady použití zaváděcího nástroje Enterprise jsou znázorněné níže a na stránce příkladů [parametrů příkazového](command-line-parameter-examples.md) řádku. Jiný jazyk než angličtinu můžete nainstalovat tak, že ze seznamu jazykových národního prostředí změníte národní prostředí na národní prostředí. K dalšímu přizpůsobení mezipaměti můžete použít seznam komponent `en-US` a úloh. [](#list-of-language-locales) [](workload-and-component-ids.md)

> [!TIP]
> Pokud chcete zabránit chybě, ujistěte se, že je úplná instalační cesta kratší než 80 znaků.

- Pro vývoj webových a desktopových aplikací .NET spusťte:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Pro vývoj desktopových aplikací a Office v .NET spusťte:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Pro vývoj desktopových aplikací v jazyce C++ spusťte:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Pokud chcete vytvořit úplné místní rozložení jenom v angličtině se všemi funkcemi (bude to trvat dlouhou dobu, máme spoustu &mdash; funkcí!),  spusťte:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Úplné rozložení Visual Studio vyžaduje minimálně 35 GB místa na disku. Další informace najdete v tématu [Požadavky na systém.](/visualstudio/productinfo/vs2017-system-requirements-vs/) 

::: moniker-end

::: moniker range=">=vs-2019"

   > [!NOTE]
   > Úplné rozložení Visual Studio vyžaduje minimálně 41 GB místa na disku. Další informace najdete v tématu [Požadavky na systém.](/visualstudio/releases/2019/system-requirements/)

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 – Visual Studio z místní mezipaměti
Když instalujete Visual Studio z místní instalační mezipaměti, instalační Visual Studio používá verze souborů uložené v místní mezipaměti. Pokud ale během instalace vyberete komponenty, které nejsou v mezipaměti, instalační Visual Studio se je pokusí stáhnout z internetu. Abyste měli jistotu, že instalujete jenom soubory, které [](use-command-line-parameters-to-install-visual-studio.md) jste si předtím stáhli, použijte stejné možnosti příkazového řádku, které jste použili k vytvoření mezipaměti rozložení. 

Pokud jste například vytvořili místní mezipaměť instalace pomocí následujícího příkazu:

```shell
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Pak pomocí tohoto příkazu spusťte instalaci:

```shell
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> Pokud používáte aplikaci Visual Studio Community, musíte ji aktivovat přihlášením k produktu do 30 dnů od instalace. Aktivace vyžaduje připojení k internetu.

> [!NOTE]
> Pokud se zobrazí chyba s neplatným podpisem, musíte [nainstalovat aktualizované certifikáty](install-certificates-for-visual-studio-offline.md). Otevřete složku Certifikáty ve vaší offline mezipaměti. Poklikejte na jednotlivé soubory certifikátů a pak proklikejte průvodce Správcem certifikátů. Pokud se zobrazí dotaz na heslo, ponechte ho prázdné.

::: moniker range=">=vs-2019"
> [!TIP]
> Pokud se u offline instalací zobrazí chybová zpráva "Produkt odpovídající následujícím parametrům se nenašel", ujistěte se, že používáte přepínač s verzí `--noweb` 16.3.5 nebo novější.

::: moniker-end

### <a name="list-of-language-locales"></a>Seznam jazykových národního prostředí

| **Národní prostředí jazyka** | **Jazyk**          |
|---------------------|-----------------------|
| cs-CZ               | Čeština                 |
| de-DE               | Němčina                |
| en-US               | Angličtina               |
| es-ES               | Španělština               |
| fr-FR               | Francouzština                |
| it-IT               | Italština               |
| ja-JP               | Japonština              |
| ko-KR               | Korejština                |
| pl-PL               | Polština                |
| pt-BR               | Portugalština – Brazílie   |
| ru-RU               | Ruština               |
| tr-TR               | Turečtina               |
| zh-CN               | Čínština – zjednodušená  |
| zh-TW               | Čínština – tradiční |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

- [Vytvoření síťové instalace sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Instalace certifikátů vyžadovaných pro instalaci sady Visual Studio offline](../install/install-certificates-for-visual-studio-offline.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
