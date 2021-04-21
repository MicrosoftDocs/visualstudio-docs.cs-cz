---
title: Vytvoření offline instalace
description: Přečtěte si, jak nainstalovat Visual Studio offline, když máte nespolehlivé připojení k Internetu nebo malou šířku pásma.
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
ms.openlocfilehash: c37ccb9c6dce1f6b20b8ade317e8135462c65011
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800869"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Vytvoření offline instalace sady Visual Studio

::: moniker range="vs-2017"

Navrhli jsme sadu Visual Studio 2017, aby dobře fungovala v nejrůznějších konfiguracích sítě a počítačů. Doporučujeme vám, abyste si vyzkoušeli [webový instalační program sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads) &mdash; , což je malý soubor, který vám umožní zůstat v aktuálním prostředí se všemi nejnovějšími opravami a funkcemi &mdash; , které chápeme, že nemůžete být schopni.

::: moniker-end

::: moniker range="vs-2019"

Navrhli jsme sadu Visual Studio 2019, aby dobře fungovala v nejrůznějších konfiguracích sítě a počítačů. Doporučujeme vám, abyste si vyzkoušeli [webový instalační program sady Visual Studio](https://visualstudio.microsoft.com/downloads) &mdash; , což je malý soubor, který vám umožní zůstat v aktuálním prostředí se všemi nejnovějšími opravami a funkcemi &mdash; , které chápeme, že nemůžete být schopni.

::: moniker-end

Například můžete mít nespolehlivé připojení k Internetu nebo jeden, který má malou šířku pásma. Pokud ano, máte k dispozici několik možností: můžete použít novou funkci stáhnout vše, potom nainstalovat a stáhnout soubory před instalací nebo můžete použít příkazový řádek k vytvoření místní mezipaměti souborů.

> [!NOTE]
> Pokud jste podnikovým správcem, který chce provést nasazení sady Visual Studio do sítě klientských pracovních stanic, které jsou brány firewall z Internetu, přečtěte si článek [Vytvoření síťové instalace sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md) a [nainstalujte certifikáty vyžadované pro instalační stránky systému Visual Studio pro offline instalaci](../install/install-certificates-for-visual-studio-offline.md) .

## <a name="use-the-download-all-then-install-feature"></a>Použijte funkci stáhnout vše a pak nainstalovat.

::: moniker range="vs-2017"

[**Novinka ve verzi 15,8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): po stažení webového instalačního programu vyberte možnost nový **Stáhnout vše a pak** z instalační program pro Visual Studio nainstalujte. Pak pokračujte v instalaci.

   ![Možnost stáhnout vše a pak nainstalovat](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Po stažení webového instalačního programu vyberte možnost nové **Stáhnout vše a pak** z instalační program pro Visual Studio nainstalovat. Pak pokračujte v instalaci.

   ![Možnost stáhnout vše a pak nainstalovat](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Navrhli jsme funkci stáhnout vše a pak nainstalovat, abyste mohli Visual Studio stáhnout jako jednu instalaci pro stejný počítač, na který jste ho stáhli. Tímto způsobem se můžete bezpečně odpojit od webu před instalací sady Visual Studio.

> [!IMPORTANT]
> Nepoužívejte funkci stáhnout vše a potom nainstalovat a vytvořte offline mezipaměť, kterou chcete přenést do jiného počítače. Tento postup není navržený tak, aby fungoval. <br><br>Pokud chcete vytvořit offline mezipaměť v místním počítači, kterou pak můžete použít k instalaci sady Visual Studio, přečtěte si část [použití příkazového řádku k vytvoření místní mezipaměti](#use-the-command-line-to-create-a-local-cache) .  Alternativně stránka [vytvořit síťovou instalaci sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md) poskytuje informace o tom, jak vytvořit mezipaměť v síti.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Použití příkazového řádku k vytvoření místní mezipaměti
::: moniker range="vs-2017"

Po stažení malého zaváděcího nástroje použijte příkazový řádek k vytvoření místní mezipaměti. Pak použijte místní mezipaměť pro instalaci sady Visual Studio. (Tento proces nahrazuje soubory ISO, které byly k dispozici pro předchozí verze). 

::: moniker-end

::: moniker range="vs-2019"

Po stažení malého souboru zaváděcího nástroje použijte příkazový řádek k vytvoření místní mezipaměti. Pak použijte místní mezipaměť pro instalaci sady Visual Studio.

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 – stažení zaváděcího nástroje sady Visual Studio

K dokončení tohoto kroku je nutné připojení k Internetu.

::: moniker range="vs-2017"

Chcete-li získat nejnovější zaváděcí nástroj pro sadu Visual Studio 2017 verze 15,9, navštivte stránku [předchozí verze sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) a Stáhněte jeden z následujících souborů zaváděcího nástroje: 

| Edice | Bitmap |
|-------------|-----------------------|
|Verze Visual Studio Professional 2017 15,9 | vs_professional.exe |
|Verze Visual Studio Enterprise 2017 15,9 | vs_enterprise.exe |
|Verze Visual Studio Build Tools 2017 15,9  | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Začněte stažením zaváděcího nástroje sady Visual Studio 2019 ze [stránky stažení sady Visual](https://visualstudio.microsoft.com/downloads) Studio nebo ze stránky [verze sady Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) pro vaši zvolenou verzi a edici sady Visual Studio. Instalační soubor &mdash; nebo zaváděcí nástroj se &mdash; bude shodovat s jedním z následujících způsobů:

| Edice                    | Soubor                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Komunita sady Visual Studio 2019    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Nástroje pro sestavení sady Visual Studio 2019   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit, jakou verzi je, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přečtěte si stránku [čísla sestavení sady Visual Studio a data verzí](visual-studio-build-numbers-and-release-dates.md) .

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přečtěte si stránku [vydání sady Visual studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history) .

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>Krok 2 – Vytvoření místní mezipaměti instalace

K dokončení tohoto kroku je nutné připojení k Internetu.

Otevřete příkazový řádek a pomocí parametrů zaváděcího nástroje, jak je definováno v [parametrech příkazového řádku pro instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md) , použijte k vytvoření místní mezipaměti instalace. Běžné příklady použití zaváděcího nástroje Enterprise jsou uvedené níže a na stránce [Příklady parametrů příkazového řádku](command-line-parameter-examples.md) . Jiný jazyk než angličtinu můžete nainstalovat tak, že změníte `en-US` národní prostředí ze [seznamu jazykových národních prostředí](#list-of-language-locales)a můžete k dalšímu přizpůsobení mezipaměti použít [seznam komponent a úloh](workload-and-component-ids.md) .

> [!TIP]
> Aby se zabránilo chybě, ujistěte se, že úplná cesta k instalaci je kratší než 80 znaků.

- Pro vývoj pro web a .NET pro desktopové prostředí .NET spusťte:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Pro vývoj pro Desktop a Office v .NET spusťte:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Pro vývoj desktopových aplikací pro C++ spusťte:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Pro vytvoření kompletního místního rozložení, jenom v angličtině, se všemi funkcemi (Tato akce bude trvat dlouhou dobu, &mdash; máme _spoustu_ funkcí!) spusťte:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku. Další informace najdete v tématu [požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs/). 

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku. Další informace najdete v tématu [požadavky na systém](/visualstudio/releases/2019/system-requirements/).

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 – instalace sady Visual Studio z místní mezipaměti
Při instalaci sady Visual Studio z místní mezipaměti instalace používá instalační program sady Visual Studio místní verze souborů v mezipaměti. Pokud ale během instalace vyberete komponenty, které v mezipaměti nejsou, pak se instalační program sady Visual Studio pokusí o stažení z Internetu. Abyste měli jistotu, že nainstalujete jenom soubory, které jste stáhli dříve, použijte stejné [Možnosti příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) , které jste použili k vytvoření mezipaměti rozložení. 

Pokud jste například vytvořili mezipaměť místní instalace pomocí následujícího příkazu:

```cmd
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Potom pomocí tohoto příkazu spusťte instalaci:

```cmd
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> Pokud používáte sadu Visual Studio Community, musíte ji aktivovat přihlášením k produktu do 30 dnů od instalace. Aktivace vyžaduje připojení k Internetu.

> [!NOTE]
> Pokud se zobrazí chyba, že signatura není platná, musíte [nainstalovat aktualizované certifikáty](install-certificates-for-visual-studio-offline.md). Otevřete složku certifikáty v offline mezipaměti. Dvakrát klikněte na jednotlivé soubory certifikátů a potom klikněte na Průvodce správcem certifikátů. Pokud se zobrazí výzva k zadání hesla, ponechte prázdné.

::: moniker range="vs-2019"
> [!TIP]
> V případě instalace offline se zobrazí chybová zpráva s informacemi o tom, že produkt odpovídající následujícím parametrům nebyl nalezen, ujistěte se, že používáte `--noweb` přepínač s verzí 16.3.5 nebo novější.

::: moniker-end

### <a name="list-of-language-locales"></a>Seznam jazykových národních prostředí

| **Jazyk – národní prostředí** | **Jazyk** |
| ----------------------- | --------------- |
| cs-CZ | Čeština |
| de-DE | Němčina |
| en-US | Angličtina |
| es-ES | Španělština |
| fr-FR | Francouzština |
| it-IT | Italština |
| ja-JP | Japonština |
| ko-KR | Korejština |
| pl-PL | Polština |
| pt-BR | Portugalština – Brazílie |
| ru-RU | Ruština |
| tr-TR | Turečtina |
| zh-CN | Čínština – zjednodušená |
| zh-TW | Čínština – tradiční |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

- [Vytvoření síťové instalace sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Instalace certifikátů vyžadovaných pro instalaci sady Visual Studio offline](../install/install-certificates-for-visual-studio-offline.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
