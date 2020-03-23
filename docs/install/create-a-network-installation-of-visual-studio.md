---
title: Vytvoření síťové instalace
description: Přečtěte si, jak vytvořit instalační bod sítě pro nasazení sady Visual Studio v rámci rozlehlé sítě.
ms.date: 10/29/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bc31b6c5286e5d02d5fd6d4da441a001f190de90
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303405"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Vytvoření síťové instalace sady Visual Studio

Správce rozlehlé sítě obvykle vytvoří bod instalace sítě, který se bude nasazovat do klientských pracovních stanic. Visual Studio jsme navrhli tak, aby vám umožnilo ukládat soubory do mezipaměti pro počáteční instalaci spolu se všemi aktualizacemi produktů do jedné složky. (Tento proces se také označuje jako _vytvoření rozložení_.)

Udělali jsme to tak, aby klientské pracovní stanice mohly ke správě instalace používat stejné síťové umístění, i když ještě nebyly aktualizovány na nejnovější aktualizaci obsluhy.

 > [!NOTE]
 > Pokud máte více edic sady Visual Studio v rámci rozlehlé sítě (například Visual Studio Professional a Visual Studio Enterprise), musíte vytvořit samostatnou sdílenou síťovou instalaci pro každou edici.

## <a name="download-the-visual-studio-bootstrapper"></a>Stažení zaváděcího nástroje sady Visual Studio

Stáhněte si soubor zaváděcího nástroje pro požadovanou edici sady Visual Studio. Ujistěte se, že jste **zvolili Uložit**a pak zvolte **Otevřít složku**.

::: moniker range="vs-2017"

Pokud chcete získat zaváděcí nástroj pro Visual Studio 2017, podívejte se na stránku pro stažení [předchozích verzí Visual Studia,](https://visualstudio.microsoft.com/vs/older-downloads/) kde najdete podrobnosti o tom, jak to udělat.

Váš spustitelný&mdash;soubor nastavení nebo být konkrétnější,&mdash;soubor zaváděcího nástroje by měl odpovídat nebo být podobný jedné z následujících.

| Edice | Název_souboru |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Build Tools   | **vs_buildtools.exe** |

Mezi další podporované zaváděcí nástroje patří **vs_feedbackclient.exe**, **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe**a **vs_testprofessional.exe**.

::: moniker-end

::: moniker range="vs-2019"

Váš spustitelný&mdash;soubor nastavení nebo být konkrétnější,&mdash;zaváděcí soubor by měl odpovídat nebo být podobné jedné z následujících.

|Edice | Stáhnout|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Mezi další podporované zaváděcí nástroje patří [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)a [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, je toto postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem myši na soubor zaváděcího nástroje, zvolte **Vlastnosti**, zvolte kartu **Podrobnosti** a pak zobrazte číslo **verze produktu.** Chcete-li toto číslo porovnat s verzí sady Visual Studio, podívejte se na stránku [čísla sestavení sady Visual Studio a data vydání.](visual-studio-build-numbers-and-release-dates.md)

## <a name="create-an-offline-installation-folder"></a>Vytvoření složky instalace offline

K dokončení tohoto kroku musíte mít připojení k internetu. Chcete-li vytvořit offline instalaci se všemi jazyky a funkcemi, použijte příkaz, který je podobný jednomu z následujících příkladů.

   > [!IMPORTANT]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku a stažení může nějakou dobu trvat. Podrobnosti o vytvoření rozložení s pouze součástmi, které chcete nainstalovat, naleznete v části [Přizpůsobení rozložení sítě.](#customize-the-network-layout)
   >
   > [!TIP]
   > Ujistěte se, že jste příkaz spouštěli z adresáře Ke stažení. Obvykle je to `C:\Users\<username>\Downloads` v počítači se systémem Windows 10.

- Pro Visual Studio Enterprise spusťte:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Pro Visual Studio Professional spusťte:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Změna souboru response.json

Soubor response.json můžete upravit a nastavit výchozí hodnoty, které se používají při spuštění instalace.  Můžete například nakonfigurovat `response.json` soubor tak, aby vyvoloval určitou sadu úloh vybraných automaticky. Podrobnosti [najdete v tématu Automatizace instalace sady Visual Studio se souborem odpovědí.](automated-installation-with-response-file.md)

A pokud narazíte na problém s zaváděcí nástroj Visual Studio vyvolání chyby při spárování se souborem response.json, naleznete v části "Nepodařilo se analyzovat ID z nadřazeného procesu" [řešení problémů souvisejících se sítí při instalaci nebo použití](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) stránky Visual Studio další informace o tom, co dělat.

## <a name="copy-the-layout-to-a-network-share"></a>Kopírování rozložení do sdílené síťové složky

Hostujte rozložení ve sdílené síťové složce, aby ji bylo možné spustit z jiných počítačů.

Následující příklad používá [xcopy](/windows-server/administration/windows-commands/xcopy/). Můžete také použít [robocopy](/windows-server/administration/windows-commands/robocopy/), pokud si budete přát.  

::: moniker range="vs-2017"

Příklad:

```cmd
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> Chcete-li zabránit chybě, ujistěte se, že úplná cesta rozložení je menší než 80 znaků.

## <a name="customize-the-network-layout"></a>Přizpůsobení rozložení sítě

Existuje několik možností, které můžete použít k přizpůsobení rozložení sítě. Můžete vytvořit částečné rozložení, které obsahuje pouze určitou sadu [národních prostředí jazyků](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [úloh, součástí a jejich doporučených nebo volitelných závislostí](workload-and-component-ids.md). To může být užitečné, pokud víte, že budete nasazovat pouze podmnožinu úloh do klientských pracovních stanic. Mezi typické parametry příkazového řádku pro přizpůsobení rozložení patří:

* `--add`pro určení [pracovního vytížení nebo ID součástí](workload-and-component-ids.md). <br>Pokud `--add` se používá, jsou staženy pouze `--add` ty úlohy a součásti určené s.  Pokud `--add` se nepoužívá, stáhnou se všechny úlohy a součásti.
* `--includeRecommended`zahrnout všechny doporučené součásti pro zadaná ID pracovního vytížení
* `--includeOptional`zahrnout všechny doporučené a volitelné součásti pro zadané ID pracovního vytížení.
* `--lang`chcete-li určit [národní prostředí jazyka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Zde je několik příkladů, jak vytvořit vlastní částečné rozložení.

* Chcete-li stáhnout všechny úlohy a součásti pouze pro jeden jazyk, spusťte:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Chcete-li stáhnout všechny úlohy a součásti pro více jazyků, spusťte:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Chcete-li stáhnout jednu úlohu pro všechny jazyky, spusťte:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Chcete-li stáhnout dvě úlohy a jednu volitelnou komponentu pro tři jazyky, spusťte:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Stažení dvou úloh a všech doporučených součástí:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Chcete-li stáhnout dvě úlohy a všechny jejich doporučené a volitelné součásti, spusťte:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Novinka ve verzi 15.3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Uložení možností rozložení

::: moniker-end

Při spuštění příkazu rozložení se uloží zadané možnosti (například úlohy a jazyky). Následné příkazy rozložení budou obsahovat všechny předchozí možnosti.  Zde je příklad rozložení s jedním zatížením pouze pro angličtinu:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Pokud chcete aktualizovat toto rozložení na novější verzi, není nutné zadávat žádné další parametry příkazového řádku. Předchozí nastavení jsou uložena a používána všemi následujícími příkazy rozložení v této složce rozložení.  Následující příkaz aktualizuje existující částečné rozložení.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Pokud chcete přidat další úlohy, tady je příklad, jak to udělat. V takovém případě přidáme úlohy Azure a lokalizovaný jazyk.  Nyní spravované plochy a Azure jsou zahrnuty v tomto rozložení.  Jazykové prostředky pro angličtinu a němčinu jsou zahrnuty pro všechny tyto úlohy. Rozložení je aktualizováno na nejnovější dostupnou verzi.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Pokud chcete aktualizovat existující rozložení na úplné rozložení, použijte možnost --all, jak je znázorněno v následujícím příkladu.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Nasazení ze síťové instalace

Správci mohou nasadit aplikaci Visual Studio na klientské pracovní stanice jako součást instalačního skriptu. Nebo uživatelé, kteří mají práva správce můžete spustit instalační program přímo ze sdílené složky k instalaci sady Visual Studio na svém počítači.

* Uživatelé mohou nainstalovat spuštěním následujícího příkazu: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Správci mohou instalovat v bezobslužném režimu spuštěním následujícího příkazu:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Chcete-li zabránit chybě, ujistěte se, že úplná cesta rozložení je menší než 80 znaků.

> [!TIP]
> Při spuštění jako součást dávkového `--wait` souboru, možnost `vs_enterprise.exe` zajišťuje, že proces čeká na dokončení instalace před vrátí ukončovací kód.
>
> To je užitečné v případě, že správce rozlehlé sítě chce provést další akce s dokončenou instalací (například [použít kód Product Key na úspěšnou instalaci),](automatically-apply-product-keys-when-deploying-visual-studio.md)ale musí počkat na dokončení instalace, aby zpracovat návratový kód z této instalace.
>
> Pokud nepoužijete `--wait`, `vs_enterprise.exe` proces ukončí před dokončením instalace a vrátí nepřesný ukončovací kód, který nepředstavuje stav operace instalace.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> Pokud se u offline instalací zobrazí chybová zpráva "Produkt odpovídající následujícím parametrům nebyl nalezen", `--noweb` ujistěte se, že používáte přepínač s verzí 16.3.5 nebo novější.
>
::: moniker-end

Při instalaci z rozložení je nainstalovaný obsah získán z rozložení. Pokud však vyberete komponentu, která není v rozvržení, bude získána z internetu.  Pokud chcete zabránit nastavení sady Visual Studio ve stahování obsahu, který `--noWeb` chybí v rozložení, použijte tuto možnost. Pokud `--noWeb` je použit a v rozvržení chybí veškerý obsah, který je vybrán k instalaci, instalace se nezdaří.

> [!IMPORTANT]
> Tato `--noWeb` možnost nezabrání nastavení sady Visual Studio v kontrole aktualizací. Další informace naleznete na stránce [Řízení aktualizací nasazení sady Visual Studio v síti.](controlling-updates-to-visual-studio-deployments.md)

### <a name="error-codes"></a>Kódy chyb

Pokud jste `--wait` použili parametr, pak v závislosti `%ERRORLEVEL%` na výsledku operace je proměnná prostředí nastavena na jednu z následujících hodnot:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Aktualizace rozložení instalace sítě

Jakmile budou k dispozici aktualizace produktů, můžete [aktualizovat rozložení instalace sítě](update-a-network-installation-of-visual-studio.md) tak, aby zahrnovalo aktualizované balíčky.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Jak vytvořit rozložení pro předchozí verzi sady Visual Studio

::: moniker range="vs-2017"

> [!NOTE]
> Zaváděcí nástroje Sady Visual Studio, které jsou k dispozici na [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) stáhnout a nainstalovat nejnovější verzi sady Visual Studio, která je k dispozici při každém spuštění.
>
> Takže pokud si stáhnete *zaváděcí nástroj* sady Visual Studio ještě dnes a spustíte jej za šest měsíců, nainstaluje verzi sady Visual Studio, která je aktuální v době spuštění zaváděcího nástroje.
>
> Ale pokud vytvoříte *rozložení* a potom nainstalovat z něj, rozložení nainstaluje konkrétní verzi sady Visual Studio, která existuje v rozložení. I když novější verze může existovat online, získáte verzi sady Visual Studio, která je v rozložení.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Zaváděcí nástroje Sady Visual Studio, které jsou k dispozici na [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads) stáhnout a nainstalovat nejnovější verzi sady Visual Studio, která je k dispozici při každém spuštění.
>
> Takže pokud si stáhnete *zaváděcí nástroj* sady Visual Studio ještě dnes a spustíte jej za šest měsíců, nainstaluje verzi sady Visual Studio, která je aktuální v době spuštění zaváděcího nástroje.
>
> Ale pokud vytvoříte *rozložení* a potom nainstalovat z něj, rozložení nainstaluje konkrétní verzi sady Visual Studio, která existuje v rozložení. I když novější verze může existovat online, získáte verzi sady Visual Studio, která je v rozložení.

::: moniker-end

Pokud potřebujete vytvořit rozložení pro starší verzi sady Visual [https://my.visualstudio.com](https://my.visualstudio.com) Studio, přejděte ke stažení "pevné" verze zaváděcích nástroje Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak získat podporu pro offline instalátor

Pokud narazíte na problém s offline instalací, chceme o něm vědět. Nejlepší způsob, jak nám to říct, je použít nástroj [Nahlásit problém.](../ide/how-to-report-a-problem-with-visual-studio.md) Při použití tohoto nástroje nám můžete poslat telemetrii a protokoly, které potřebujeme, aby nám pomohli diagnostikovat a opravit problém.

Nabízíme také možnost podpory [**živého chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (pouze v angličtině) pro problémy související s instalací.

Máme k dispozici i další možnosti podpory. Seznam najdete na stránce [Zpětná vazba.](../ide/feedback-options.md)

## <a name="see-also"></a>Viz také

- [Průvodce správcem sady Visual Studio](visual-studio-administrator-guide.md)
- [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Poradce při potížích se sítí při instalaci nebo použití sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Řízení aktualizací nasazení sady Visual Studio v síti](controlling-updates-to-visual-studio-deployments.md)
- [Životní cyklus produktu Visual Studio a servis](/visualstudio/releases/2019/servicing/)
- [Aktualizace sady Visual Studio v servisním směrném plánu](update-servicing-baseline.md)
- [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
