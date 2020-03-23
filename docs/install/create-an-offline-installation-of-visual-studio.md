---
title: Vytvoření offline instalace
description: Přečtěte si, jak nainstalovat Visual Studio offline, pokud máte nespolehlivé připojení k internetu nebo malou šířku pásma.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d52dd064e895b1e35230b93c85a7a8499032943e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114832"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Vytvoření offline instalace sady Visual Studio

::: moniker range="vs-2017"

Visual Studio 2017 jsme navrhli tak, aby dobře fungovalo v různých konfiguracích sítě a počítače. I když doporučujeme vyzkoušet [visual studio webový instalační program,](https://visualstudio.microsoft.com/vs/older-downloads)&mdash;který je malý soubor a&mdash;umožňuje zůstat aktuální se všemi nejnovějšími opravami a funkcemi chápeme, že nemusí být možné.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 jsme navrhli tak, aby dobře fungovalo v různých konfiguracích v síti a počítačích. I když doporučujeme vyzkoušet [visual studio webový instalační program,](https://visualstudio.microsoft.com/downloads)&mdash;který je malý soubor a&mdash;umožňuje zůstat aktuální se všemi nejnovějšími opravami a funkcemi chápeme, že nemusí být možné.

::: moniker-end

Můžete mít například nespolehlivé připojení k internetu nebo připojení s malou šířkou pásma. Pokud ano, máte několik možností: Můžete použít novou funkci "Stáhnout vše a poté nainstalovat" ke stažení souborů před instalací nebo můžete pomocí příkazového řádku vytvořit místní mezipaměť souborů.

> [!NOTE]
> Pokud jste správce rozlehlé sítě, který chce provést nasazení sady Visual Studio do sítě klientských pracovních stanic, které jsou brány firewall z Internetu, přečtěte si naše [informace o vytvoření síťové instalace](../install/create-a-network-installation-of-visual-studio.md) sady Visual Studio a instalace [certifikátů požadovaných pro offline instalační](../install/install-certificates-for-visual-studio-offline.md) stránky sady Visual Studio.

## <a name="use-the-download-all-then-install-feature"></a>Použijte funkci "Stáhnout vše a poté nainstalovat"

::: moniker range="vs-2017"

[**Novinka ve verzi 15.8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): Po stažení webového instalačního programu vyberte novou možnost **Stáhnout vše a pak nainstalovat** možnost z Instalační služby sady Visual Studio. Potom pokračujte v instalaci.

   ![Možnost "Stáhnout vše a pak nainstalovat"](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Po stažení webového instalačního programu vyberte novou možnost **Stáhnout vše a pak nainstalovat** možnost z Instalační služby sady Visual Studio. Potom pokračujte v instalaci.

   ![Možnost "Stáhnout vše a pak nainstalovat"](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Navrhli jsme funkci "Stáhnout vše a poté nainstalovat", abyste si mohli stáhnout visual studio jako jednu instalaci pro stejný počítač, do kterého jste jej stáhli. Tímto způsobem můžete bezpečně odpojit od webu před instalací sady Visual Studio.

> [!IMPORTANT]
> Nepoužívejte funkci Stáhnout vše a poté ji nainstalujte k vytvoření mezipaměti offline, kterou chcete přenést do jiného počítače. Není to navrženo tak, aby to tak fungovalo. <br><br>Pokud chcete vytvořit offline mezipaměť pro instalaci sady Visual Studio do jiného počítače, naleznete informace o vytvoření síťové mezipaměti v [Create a network installation of Visual Studio](../install/create-a-network-installation-of-visual-studio.md) části Vytvoření síťové mezipaměti v části Vytvoření místní mezipaměti na [příkazovém řádku](#use-the-command-line-to-create-a-local-cache) na této stránce.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Vytvoření místní mezipaměti pomocí příkazového řádku

Po stažení malého zaváděcího nástroje vytvořte pomocí příkazového řádku místní mezipaměť. Potom použijte místní mezipaměti k instalaci sady Visual Studio. (Tento proces nahradí soubory ISO, které byly k dispozici pro předchozí verze.)

Jak na to:

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 – Stažení zaváděcího nástroje sady Visual Studio

K dokončení tohoto kroku musíte mít připojení k internetu.

::: moniker range="vs-2017"

Pokud chcete získat zaváděcí nástroj pro Visual Studio 2017, podívejte se na stránku pro stažení [předchozích verzí Visual Studia,](https://visualstudio.microsoft.com/vs/older-downloads/) kde najdete podrobnosti o tom, jak to udělat.

Váš spustitelný&mdash;soubor nastavení nebo být konkrétnější,&mdash;soubor zaváděcího nástroje by měl odpovídat nebo být podobný jedné z následujících.

| Edice | Název_souboru |
|-------------|-----------------------|
|Visual Studio Community | vs_community.exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise.exe |
|Visual Studio Build Tools   | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Začněte stažením zaváděcího nástroje sady Visual Studio pro vybranou edici sady Visual Studio. Instalační soubor&mdash;nebo zaváděcí nástroj&mdash;se bude shodovat nebo se podobat jedné z následujících možností.

| Edice                    | File                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, je toto postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem myši na soubor zaváděcího nástroje, zvolte **Vlastnosti**, zvolte kartu **Podrobnosti** a pak zobrazte číslo **verze produktu.** Chcete-li toto číslo porovnat s verzí sady Visual Studio, podívejte se na stránku [čísla sestavení sady Visual Studio a data vydání.](visual-studio-build-numbers-and-release-dates.md)

### <a name="step-2---create-a-local-install-cache"></a>Krok 2 – Vytvoření místní mezipaměti pro instalaci

K dokončení tohoto kroku musíte mít připojení k internetu.

> [!IMPORTANT]
> Pokud nainstalujete komunitu Sady Visual Studio, je nutné ji aktivovat do 30 dnů od instalace. To vyžaduje připojení k internetu.

Otevřete příkazový řádek a použijte jeden z příkazů z následujících příkladů. Příklady, které jsou zde uvedeny, předpokládají, že používáte verzi sady Visual Studio community; upravte příkaz podle potřeby pro vaši edici.

> [!TIP]
> Chcete-li zabránit chybě, ujistěte se, že úplná instalační cesta je menší než 80 znaků.

- Pro vývoj webu a plochy .NET spusťte:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Pro vývoj aplikace .NET pro stolní počítače a Office spusťte:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Pro vývoj pracovních prostředí v jazyce C++ spusťte:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Chcete-li vytvořit kompletní místní rozložení se všemi&mdash;funkcemi (to bude trvat dlouho, máme _spoustu_ funkcí!), Spusťte:

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku. Další informace naleznete v [tématu Systémové požadavky](/visualstudio/productinfo/vs2017-system-requirements-vs/). Informace o vytvoření rozložení pouze s komponentami, které chcete nainstalovat, naleznete v [tématu Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku. Další informace naleznete v [tématu Systémové požadavky](/visualstudio/releases/2019/system-requirements/). Informace o vytvoření rozložení pouze s komponentami, které chcete nainstalovat, naleznete v [tématu Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

Chcete-li nainstalovat jiný jazyk než `en-US` angličtinu, změňte národní prostředí [ze seznamu národních prostředí jazyka](#list-of-language-locales). Potom použijte [seznam součástí a úloh, které jsou k dispozici](workload-and-component-ids.md) pro další přizpůsobení mezipaměti instalace.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 – Instalace sady Visual Studio z místní mezipaměti

> [!TIP]
> Při spuštění z místní mezipaměti instalace instalační program používá místní verze každého z těchto souborů. Pokud však během instalace vyberete součásti, které nejsou v mezipaměti, pokusí se je instalační program stáhnout z internetu.

::: moniker range="vs-2019"
> [!IMPORTANT]
> Pokud se u offline instalací zobrazí chybová zpráva "Produkt odpovídající následujícím parametrům nebyl nalezen", `--noweb` ujistěte se, že používáte přepínač s verzí 16.3.5 nebo novější.
>
::: moniker-end

Chcete-li se ujistit, že nainstalujete pouze soubory, které jste dříve stáhli, použijte stejné možnosti příkazového řádku, které jste použili k vytvoření mezipaměti rozložení. Pokud jste například vytvořili mezipaměť rozložení s následujícím příkazem:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Potom pomocí tohoto příkazu spusťte instalaci:

```cmd
c:\vslayout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

Další příklady použití [parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)naleznete v [příkladech parametrů příkazového řádku pro](command-line-parameter-examples.md) stránku instalace sady Visual Studio. 

> [!NOTE]
> Pokud se zobrazí chyba, že podpis je neplatný, je nutné nainstalovat aktualizované certifikáty. Otevřete složku Certifikáty v offline mezipaměti. Poklepejte na všechny soubory certifikátů a potom klikněte na průvodce Správce množek. Pokud budete požádáni o zadání hesla, ponechte ho prázdné.

### <a name="list-of-language-locales"></a>Seznam jazykových národních prostředí

| **Jazyk-národní prostředí** | **Jazyk** |
| ----------------------- | --------------- |
| cs-CZ | Čeština |
| de-DE | Němčina |
| cs-CZ | Angličtina |
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
| zh-TW | Čínština - tradiční |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

- [Vytvoření síťové instalace sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Instalace certifikátů požadovaných pro offline instalaci sady Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
