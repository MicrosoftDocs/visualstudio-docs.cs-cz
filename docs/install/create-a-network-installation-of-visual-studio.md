---
title: Vytvoření síťové instalace
description: Zjistěte, jak vytvořit bod instalace sítě pro nasazení sady Visual Studio v rámci organizace.
ms.date: 10/01/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 178bd693c514e42fb77c0addce3fa6c00d1bef4f
ms.sourcegitcommit: a2f1f27aa33d807b39292d65a49d8db4653491ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71709058"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Vytvoření síťové instalace sady Visual Studio

Podnikový správce obvykle vytvoří bod instalace sítě pro nasazení do klientských pracovních stanic. Navrhli jsme aplikaci Visual Studio, která vám umožní ukládat soubory do mezipaměti pro počáteční instalaci společně se všemi aktualizacemi produktu do jediné složky. (Tento proces se také označuje jako _vytvoření rozložení platného pro_.)

Jsme udělali to tak, aby pracovní stanice klienta můžete používat stejné umístění v síti ke správě jejich instalace i v případě, že ještě neprovedli aktualizaci na nejnovější servisní aktualizace.

 > [!NOTE]
 > Pokud máte víc edicí sady Visual Studio používá v rámci vaší organizace (například Visual Studio Professional i Visual Studio Enterprise), musíte vytvořit sdílenou složku instalace samostatné sítě pro jednotlivé edice.

## <a name="download-the-visual-studio-bootstrapper"></a>Stažení zaváděcího nástroje Visual Studio

Stáhněte si edici sady Visual Studio, kterou chcete. Ujistěte se, že klikněte na tlačítko **Uložit**a potom klikněte na tlačítko **otevřít složku**.

Nastavení spustitelných&mdash;nebo na konkrétnější, soubor zaváděcí nástroj&mdash;by měl odpovídat jedné z následujících akcí.

::: moniker range="vs-2017"

|Edice | Stáhnout|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
| Visual Studio Build Tools   | [vs_buildtools. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |

Mezi další podporované zaváděcí nástroje patří [vs_feedbackclient. exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_TeamExplorer. exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent. exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller. exe](https://aka.ms/vs/15/release/vs_testcontroller.exe)a [vs_testprofessional. exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

::: moniker-end

::: moniker range="vs-2019"

|Edice | Stáhnout|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [vs_buildtools. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Mezi další podporované zaváděcí nástroje patří [vs_TeamExplorer. exe](https://aka.ms/vs/16/release/vs_teamexplorer.exe), [vs_testagent. exe](https://aka.ms/vs/16/release/vs_testagent.exe)a [vs_testcontroller. exe](https://aka.ms/vs/16/release/vs_testcontroller.exe).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Vytvořte složku offline instalace

Musíte mít internetové připojení k dokončení tohoto kroku. Chcete-li vytvořit offline instalaci se všemi jazyky a všemi funkcemi, použijte příkaz, který je podobný jednomu z následujících příkladů.

   > [!IMPORTANT]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku a stažení může nějakou dobu trvat. Podrobné informace o tom, jak vytvořit rozložení jenom s součástmi, které chcete nainstalovat, najdete v části [přizpůsobení rozložení sítě](#customize-the-network-layout) .
   >
   > [!TIP]
   > Ujistěte se, spusťte příkaz z adresáře ke stažení. Obvykle to `C:\Users\<username>\Downloads` v počítači se systémem Windows 10.

- Pro Visual Studio Enterprise spusťte:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Pro sadu Visual Studio Professional spusťte:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Upravte soubor response.json

Můžete upravit response.json nastavit výchozí hodnoty, které se používají, když se spustí instalační program.  Například můžete nakonfigurovat `response.json` souboru vybrat konkrétní sadu úloh vybrat automaticky.
Zobrazit [instalace automatizace sady Visual Studio souborem odpovědí](automated-installation-with-response-file.md) podrobnosti.

## <a name="copy-the-layout-to-a-network-share"></a>Rozložení kopírovat do síťové sdílené složky

Hostování rozložení do sdílené síťové složky, aby ji můžete spustit z jiné počítače.

Následující příklad používá [xcopy](/windows-server/administration/windows-commands/xcopy/). Můžete také použít příkaz [Robocopy](/windows-server/administration/windows-commands/robocopy/), který byste měli chtít.  

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
> Aby se zabránilo chybě, ujistěte se, že cesta k celému rozložení má méně než 80 znaků.

## <a name="customize-the-network-layout"></a>Přizpůsobení rozložení sítě

Existuje několik možností, které lze použít k přizpůsobení rozvržení sítě. Lze vytvořit částečné rozložení obsahující jenom určitou sadu [národní prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [úlohy, komponenty a jejich doporučená nebo volitelné závislosti](workload-and-component-ids.md). To může být užitečné, pokud víte, že budete nasazovat pouze podmnožinu úloh do klientských pracovních stanic. Typické parametry příkazového řádku pro přizpůsobení rozložení patří:

* `--add` Chcete-li určit [ID úlohy nebo komponenty](workload-and-component-ids.md). <br>Pokud `--add` se používá, pouze úlohy a komponenty zadaným `--add` se stáhnou.  Pokud se nepoužije `--add`, stáhnou se všechny úlohy a součásti.
* `--includeRecommended` Chcete-li zahrnout všechny součásti, které jsou doporučené pro zadané ID úlohy
* `--includeOptional` Chcete-li zahrnout všechny doporučené a volitelné součásti pro zadané ID úlohy.
* `--lang` Chcete-li určit [národní prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Tady je několik příkladů toho, jak vytvořit vlastní částečné rozložení.

* Pokud chcete stáhnout všechny úlohy a komponenty pouze pro jeden jazyk, spusťte:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Pokud chcete stáhnout všechny úlohy a komponenty pro různé jazyky, spusťte:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Chcete-li stáhnout jednu úlohu pro všechny jazyky, spusťte příkaz:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Ke stažení dvou úloh a volitelnou součástí tři jazyky, spusťte:

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

### <a name="new-in-version-153"></a>Novinka ve verzi 15,3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Uložení možností rozložení

::: moniker-end

Při spuštění příkazu rozložení se uloží možnosti, které zadáte (třeba úlohy a jazyky). Rozložení následné příkazy bude obsahovat všechny předchozí možnosti.  Tady je příklad rozložení se sadou jeden pro angličtinu pouze:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Pokud chcete aktualizovat tento rozložení na novější verzi, není nutné specifikovat žádné další parametry příkazového řádku. Předchozí nastavení jsou uloženy a používány všechny následné rozložení příkazy v této složce rozložení.  Následující příkaz aktualizuje existující částečné rozložení.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Pokud chcete přidat další úlohy, tady příklad toho, jak to provést. V tomto případě přidáme sady funkcí Azure a lokalizovaný jazyk.  Teď Managed Desktop i Azure jsou zahrnuté v tomto rozvržení.  Pro všechny tyto úlohy jsou k dispozici jazykové prostředky pro angličtinu a němčinu. Rozložení se aktualizuje na nejnovější dostupnou verzi.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Pokud chcete aktualizovat existující rozložení na úplné rozložení, použijte--všechny možnosti, jak je znázorněno v následujícím příkladu.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Nasazení z síťové instalace

Správci můžou nasadit sady Visual Studio na klientských pracovních stanic, jako součást instalačního skriptu. Nebo uživatelé, kteří mají oprávnění správce, můžete spustit instalační program přímo ze sdílené složky pro instalaci sady Visual Studio na svém počítači.

* Uživatele můžete nainstalovat spuštěním následujícího příkazu: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Správci se můžou instalovat v bezobslužném režimu spuštěním následujícího příkazu:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Aby se zabránilo chybě, ujistěte se, že cesta k celému rozložení má méně než 80 znaků.
>
> [!TIP]
> Při spuštění jako součást dávkového souboru, `--wait` možnost zajišťuje, že `vs_enterprise.exe` proces čeká na dokončení instalace je dříve, než vrátí ukončovací kód.
>
> To je užitečné, pokud chce správce podnikové sítě provádět další akce instalace byla dokončena (například [použít kód product key pro úspěšnou instalaci](automatically-apply-product-keys-when-deploying-visual-studio.md)) ale musí počkat na dokončení zpracování instalace Návratový kód z této instalace.
>
> Pokud nepoužijete `--wait`, `vs_enterprise.exe` proces ukončí před dokončením instalace a vrátí nesprávné ukončovací kód, který nepředstavuje stavu operace instalace.

Při instalaci z rozložení, je obsah, který je nainstalován získaných z rozložení. Pokud však vyberete komponentu, která není v rozložení, bude získána z Internetu.  Pokud chcete zabránit ve stahování veškerý obsah, který nebyl nalezen v rozložení, použijte instalační program sady Visual Studio `--noWeb` možnost. Pokud `--noWeb` se používá a rozložení chybí veškerý obsah, který je se rozhodli nainstalovat, instalace selže.

> [!IMPORTANT]
> Možnost `--noWeb` neukončí instalaci sady Visual Studio ze zjišťování aktualizací. Další informace naleznete na stránce [ovládací prvky aktualizace pro síťové nasazení sady Visual Studio](controlling-updates-to-visual-studio-deployments.md) .

### <a name="error-codes"></a>Kódy chyb

Pokud jste použili `--wait` parametr a potom v závislosti na výsledek operace, `%ERRORLEVEL%` proměnnou prostředí je nastavená na jednu z následujících hodnot:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Aktualizace rozložení instalace sítě

Jakmile budou dostupné aktualizace produktu, můžete chtít [aktualizovat síťový diagram instalace](update-a-network-installation-of-visual-studio.md) začlenit aktualizované balíčky.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Vytvoření rozložení pro předchozí vydání sady Visual Studio

::: moniker range="vs-2017"

> [!NOTE]
> Zavaděče sady Visual Studio, které jsou k dispozici na [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) Stáhněte a nainstalujte nejnovější verzi sady Visual Studio, která je dostupná při každém spuštění.
>
> Pokud si tedy stáhnete Visual Studio *zaváděcí nástroj* ještě dnes a spustíte ho šest měsíců od tohoto okamžiku, nainstaluje se verze sady Visual Studio, která je aktuální v době spuštění zaváděcího nástroje.
>
> Pokud ale vytvoříte *rozložení* a pak z něho nainstalujete, rozložení nainstaluje konkrétní verzi sady Visual Studio, která existuje v rozložení. I když online možná existuje novější verze, získat verzi sady Visual Studio, která je v rozložení.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Zavaděče sady Visual Studio, které jsou k dispozici na [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads) Stáhněte a nainstalujte nejnovější verzi sady Visual Studio, která je dostupná při každém spuštění.
>
> Pokud si tedy stáhnete Visual Studio *zaváděcí nástroj* ještě dnes a spustíte ho šest měsíců od tohoto okamžiku, nainstaluje se verze sady Visual Studio, která je aktuální v době spuštění zaváděcího nástroje.
>
> Pokud ale vytvoříte *rozložení* a pak z něho nainstalujete, rozložení nainstaluje konkrétní verzi sady Visual Studio, která existuje v rozložení. I když online možná existuje novější verze, získat verzi sady Visual Studio, která je v rozložení.

::: moniker-end

Pokud potřebujete vytvořit rozložení pro starší verzi sady Visual Studio, přejít na [https://my.visualstudio.com](https://my.visualstudio.com) a Stáhněte si "pevné" verze spouštěcích prvků sady Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak získat podporu pro offline instalační program

Pokud dochází k potížím s offline instalací chcete vědět o něm. Nejlepší způsob, jak Řekněte nám, je použít [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) nástroj. Při použití tohoto nástroje můžete nám odeslat telemetrii a protokoly, musíme pomáhají diagnostikovat a opravit problém.

Nabízíme také [ **živý chat** ](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině) možnost podpory pro problémy související s instalací.

Další možnosti podpory dostupné, máme příliš. Seznam najdete na naší stránce s [názory na zpětnou vazbu](../ide/feedback-options.md) .

## <a name="see-also"></a>Viz také:

- [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
- [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Řízení aktualizací nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
- [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
- [Aktualizace sady Visual Studio na standardních hodnotách údržby](update-servicing-baseline.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
