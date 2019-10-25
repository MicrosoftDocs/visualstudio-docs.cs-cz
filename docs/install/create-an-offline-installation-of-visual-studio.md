---
title: Vytvoření offline instalace
description: Přečtěte si, jak nainstalovat Visual Studio offline, když máte nespolehlivé připojení k Internetu nebo malou šířku pásma.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c8b59ce38657bab157b966a25e0cd27109510215
ms.sourcegitcommit: 58000baf528da220fdf7a999d8c407a4e86c1278
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72789989"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Vytvoření offline instalace sady Visual Studio

::: moniker range="vs-2017"

Navrhli jsme sadu Visual Studio 2017, aby dobře fungovala v nejrůznějších konfiguracích sítě a počítačů. Doporučujeme, abyste si vyzkoušeli [webový instalační program sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads) , &mdash;which je malý soubor a máte možnost zůstat ve stávajícím prostředí se všemi nejnovějšími opravami a funkcemi &mdash;we pochopit, že nemůžete být schopni.

::: moniker-end

::: moniker range="vs-2019"

Navrhli jsme sadu Visual Studio 2019, aby dobře fungovala v nejrůznějších konfiguracích sítě a počítačů. Doporučujeme, abyste si vyzkoušeli [webový instalační program sady Visual Studio](https://visualstudio.microsoft.com/downloads) , &mdash;which je malý soubor a máte možnost zůstat ve stávajícím prostředí se všemi nejnovějšími opravami a funkcemi &mdash;we pochopit, že nemůžete být schopni.

::: moniker-end

Například můžete mít nespolehlivé připojení k Internetu nebo jeden, který má malou šířku pásma. Pokud ano, máte k dispozici několik možností: můžete použít novou funkci stáhnout vše, potom nainstalovat a stáhnout soubory před instalací nebo můžete použít příkazový řádek k vytvoření místní mezipaměti souborů.

> [!NOTE]
> Pokud jste podnikovým správcem, který chce provést nasazení sady Visual Studio do sítě klientských pracovních stanic, které jsou brány firewall z Internetu, přečtěte si článek [Vytvoření síťové instalace sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md) a [Instalace certifikátů. vyžaduje se pro instalační stránky offline sady Visual Studio](../install/install-certificates-for-visual-studio-offline.md) .

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
> Nepoužívejte funkci stáhnout vše a potom nainstalovat a vytvořte offline mezipaměť, kterou chcete přenést do jiného počítače. Tento postup není navržený tak, aby fungoval. <br><br>Pokud chcete vytvořit offline mezipaměť pro instalaci sady Visual Studio na jiném počítači, přečtěte si část [použití příkazového řádku k vytvoření místní mezipaměti](#use-the-command-line-to-create-a-local-cache) na této stránce, kde najdete informace o tom, jak vytvořit místní mezipaměť nebo jak [vytvořit síťovou instalaci Visual. ](../install/create-a-network-installation-of-visual-studio.md)Na stránce studia najdete informace o tom, jak vytvořit síťovou mezipaměť.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Použití příkazového řádku k vytvoření místní mezipaměti

Po stažení malého zaváděcího nástroje použijte příkazový řádek k vytvoření místní mezipaměti. Pak použijte místní mezipaměť pro instalaci sady Visual Studio. (Tento proces nahradí soubory ISO, které byly k dispozici pro předchozí verze.)

Tady je postup.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 – stažení zaváděcího nástroje sady Visual Studio

K dokončení tohoto kroku je nutné připojení k Internetu.

::: moniker range="vs-2017"

Další informace o tom, jak to udělat, najdete na stránce pro stažení [předchozích verzí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , kde můžete získat zaváděcí nástroj pro visual Studio 2017.

Spustitelný soubor instalačního programu &mdash;or tak, aby byl konkrétnější, &mdash;should soubor zaváděcího nástroje se shodují nebo se podobá jednomu z následujících.

| Edice | Bitmap |
|-------------|-----------------------|
|Visual Studio Community | vs_community. exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise. exe |
|Visual Studio Build Tools   | vs_buildtools. exe |

::: moniker-end

::: moniker range="vs-2019"

Začněte stažením zaváděcího nástroje sady Visual Studio pro zvolenou edici sady Visual Studio. Instalační soubor &mdash;or &mdash;will se shoduje s jedním z následujících způsobů.

| Edice                    | Soubor                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Build Tools   | [vs_buildtools. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přejděte na stránku [čísla sestavení sady Visual Studio a data verzí](visual-studio-build-numbers-and-release-dates.md) .

### <a name="step-2---create-a-local-install-cache"></a>Krok 2 – Vytvoření místní mezipaměti instalace

K dokončení tohoto kroku je nutné připojení k Internetu.

> [!IMPORTANT]
> Pokud nainstalujete Visual Studio Community, musíte ho aktivovat do 30 dnů od instalace. To vyžaduje připojení k Internetu.

Otevřete příkazový řádek a použijte jeden z příkazů z následujících příkladů. Příklady, které jsou zde uvedeny, předpokládají, že používáte edici Community sady Visual Studio; Upravte příkaz tak, aby odpovídal vaší edici.

> [!TIP]
> Aby se zabránilo chybě, ujistěte se, že úplná cesta k instalaci je kratší než 80 znaků.

- Pro vývoj pro web a .NET pro desktopové prostředí .NET spusťte:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Pro vývoj pro Desktop a Office v .NET spusťte:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Pro C++ vývoj desktopových aplikací spusťte:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Pokud chcete vytvořit úplné místní rozložení se všemi funkcemi (to může trvat dlouhou dobu &mdash;we bude mít _spoustu_ funkcí!), spusťte:

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku. Další informace najdete v tématu [požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs/). A informace o tom, jak vytvořit rozložení pouze s komponentami, které chcete nainstalovat, naleznete v tématu [použití parametrů příkazového řádku pro instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku. Další informace najdete v tématu [požadavky na systém](/visualstudio/releases/2019/system-requirements/). A informace o tom, jak vytvořit rozložení pouze s komponentami, které chcete nainstalovat, naleznete v tématu [použití parametrů příkazového řádku pro instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

Pokud chcete nainstalovat jiný jazyk než angličtinu, změňte `en-US` na národní prostředí ze [seznamu jazykových národních prostředí](#list-of-language-locales). Pak použijte [seznam komponent a úloh, které jsou k dispozici](workload-and-component-ids.md) k dalšímu přizpůsobení mezipaměti instalace.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 – instalace sady Visual Studio z místní mezipaměti

> [!TIP]
> Při spuštění z místní mezipaměti instalace používá instalační program místní verze každého z těchto souborů. Pokud ale během instalace vyberete komponenty, které nejsou v mezipaměti, pokusí se instalační program stáhnout z Internetu.

::: moniker range="vs-2019"
> [!IMPORTANT]
> V případě instalace offline se zobrazí chybová zpráva s informacemi o tom, že produkt odpovídající následujícím parametrům nebyl nalezen, ujistěte se, že používáte přepínač `--noweb` s verzí 16.3.5 nebo novější.
>
::: moniker-end

Abyste měli jistotu, že nainstalujete jenom soubory, které jste stáhli dříve, použijte stejné možnosti příkazového řádku, které jste použili k vytvoření mezipaměti rozložení. Například pokud jste vytvořili mezipaměť rozložení pomocí následujícího příkazu:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Potom pomocí tohoto příkazu spusťte instalaci:

```cmd
c:\vslayout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

Další příklady použití [parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)naleznete na stránce s [Příklady parametrů příkazového řádku pro instalaci sady Visual Studio](command-line-parameter-examples.md) . 

> [!NOTE]
> Pokud se zobrazí chyba, že signatura není platná, musíte nainstalovat aktualizované certifikáty. Otevřete složku certifikáty v offline mezipaměti. Dvakrát klikněte na jednotlivé soubory certifikátů a potom klikněte na Průvodce správcem certifikátů. Pokud se zobrazí výzva k zadání hesla, ponechte prázdné.

### <a name="list-of-language-locales"></a>Seznam jazykových národních prostředí

| **Jazyk – národní prostředí** | **Jazyk** |
| ----------------------- | --------------- |
| cs-CZ | Čeština |
| de-DE | Němčina |
| EN-US | Angličtina |
| ES-ES | Španělština |
| fr-FR | Francouzština |
| IT oddělení IT | Italština |
| ja-JP | Japonština |
| ko – KR | Korejština |
| pl-PL | Polština |
| pt – BR | Portugalština – Brazílie |
| ru-RU | Ruština |
| tr – TR | Turečtina |
| zh-CN | Čínština (zjednodušená) |
| zh – TW | Čínština (tradiční) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

- [Vytvoření síťové instalace sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Instalace certifikátů vyžadovaných pro instalaci sady Visual Studio offline](../install/install-certificates-for-visual-studio-offline.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
