---
title: Vytvoření síťové instalace
description: Zjistěte, jak vytvořit bod instalace sítě pro nasazení sady Visual Studio v rámci organizace.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410105"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Vytvoření síťové instalace sady Visual Studio

Podnikový správce obvykle vytvoří bod instalace sítě pro nasazení do klientských pracovních stanic. Navrhli jsme aplikaci Visual Studio, která vám umožní ukládat soubory do mezipaměti pro počáteční instalaci společně se všemi aktualizacemi produktu do jediné složky. (Tento proces je také označován jako _Vytvoření rozložení_.)

Jsme udělali to tak, aby pracovní stanice klienta můžete používat stejné umístění v síti ke správě jejich instalace i v případě, že ještě neprovedli aktualizaci na nejnovější servisní aktualizace.

 > [!NOTE]
 > Pokud máte víc edicí sady Visual Studio používá v rámci vaší organizace (například Visual Studio Professional i Visual Studio Enterprise), musíte vytvořit sdílenou složku instalace samostatné sítě pro jednotlivé edice.

## <a name="download-the-visual-studio-bootstrapper"></a>Stažení zaváděcího nástroje Visual Studio

Stáhněte si soubor zaváděcího nástroje pro edici sady Visual Studio, kterou chcete. Nezapomeňte zvolit možnost **Uložit**a pak zvolte možnost **Otevřít složku**.

::: moniker range="vs-2017"

Další informace o tom, jak to udělat, najdete na stránce pro stažení [předchozích verzí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , kde můžete získat zaváděcí nástroj pro visual Studio 2017.

Spustitelný soubor instalace&mdash;nebo má být konkrétnější,&mdash;souboru zaváděcího nástroje by se měla shodovat s jedním z následujících způsobů.

| Edition (Edice) | Název souboru |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise. exe** |
|Visual Studio Professional | **vs_professional. exe** |
|Visual Studio Build Tools   | **vs_buildtools. exe** |

Mezi další podporované zaváděcí nástroje patří **vs_feedbackclient. exe**, **vs_TeamExplorer. exe**, **vs_testagent. exe**, **vs_testcontroller. exe**a **vs_testprofessional. exe**.

::: moniker-end

::: moniker range="vs-2019"

Spustitelný soubor instalace&mdash;nebo má být konkrétnější,&mdash;soubor zaváděcího nástroje by se měl shodovat nebo být podobný jednomu z následujících.

|Edition (Edice) | Ke stažení|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Mezi další podporované zaváděcí nástroje patří [vs_TeamExplorer. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)a [vs_testcontroller. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přejděte na stránku [čísla sestavení sady Visual Studio a data verzí](visual-studio-build-numbers-and-release-dates.md) .

## <a name="create-an-offline-installation-folder"></a>Vytvořte složku offline instalace

Musíte mít internetové připojení k dokončení tohoto kroku. Chcete-li vytvořit offline instalaci se všemi jazyky a všemi funkcemi, použijte příkaz, který je podobný jednomu z následujících příkladů.

   > [!IMPORTANT]
   > Kompletní rozložení sady Visual Studio vyžaduje minimálně 35 GB místa na disku a stažení může nějakou dobu trvat. Podrobné informace o tom, jak vytvořit rozložení jenom s součástmi, které chcete nainstalovat, najdete v části [přizpůsobení rozložení sítě](#customize-the-network-layout) .
   >
   > [!TIP]
   > Ujistěte se, spusťte příkaz z adresáře ke stažení. To je obvykle `C:\Users\<username>\Downloads` na počítači se systémem Windows 10.

- Pro Visual Studio Enterprise spusťte:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Pro sadu Visual Studio Professional spusťte:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Upravte soubor response.json

Můžete upravit response.json nastavit výchozí hodnoty, které se používají, když se spustí instalační program.  Můžete třeba nakonfigurovat `response.json` soubor a vybrat konkrétní sadu úloh, které se automaticky vybraly. Podrobnosti najdete v tématu [Automatizace instalace sady Visual Studio se souborem odpovědí](automated-installation-with-response-file.md) .

A pokud narazíte na problém s zaváděcím nástrojem sady Visual Studio při párování se souborem Response. JSON dojde k chybě, přečtěte si část "selhání analýzy ID z nadřazeného procesu" v tématu [řešení potíží souvisejících se sítí při instalaci nebo použití stránky sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) , kde najdete další informace o tom, co dělat.

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

Existuje několik možností, které lze použít k přizpůsobení rozvržení sítě. Můžete vytvořit částečné rozložení, které obsahuje pouze konkrétní sadu [jazykových prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [zatížení, komponenty a jejich doporučené nebo volitelné závislosti](workload-and-component-ids.md). To může být užitečné, pokud víte, že budete nasazovat pouze podmnožinu úloh do klientských pracovních stanic. Typické parametry příkazového řádku pro přizpůsobení rozložení patří:

* `--add` určit [ID úlohy nebo komponenty](workload-and-component-ids.md). <br>Pokud se používá `--add`, stáhnou se jenom úlohy a součásti, které jsou určené `--add`.  Pokud se `--add` nepoužívá, stáhnou se všechny úlohy a součásti.
* `--includeRecommended` zahrnout všechny Doporučené součásti pro zadaná ID úloh
* `--includeOptional` zahrnout všechny doporučené a volitelné komponenty pro zadaná ID úloh.
* `--lang` určit [národní prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

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

> [!TIP]
> Při spuštění jako součást dávkového souboru zajistí možnost `--wait`, že proces `vs_enterprise.exe` počká, dokud nebude instalace dokončena, než vrátí ukončovací kód.
>
> To je užitečné v případě, že podnikový správce chce provést další akce při dokončené instalaci (například při [použití kódu Product Key pro úspěšnou instalaci](automatically-apply-product-keys-when-deploying-visual-studio.md)), ale musí počkat na dokončení instalace pro zpracování návratového kódu z této instalace.
>
> Pokud nepoužíváte `--wait`, proces `vs_enterprise.exe` se ukončí před dokončením instalace a vrátí nepřesný ukončovací kód, který nepředstavuje stav operace instalace.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> V případě instalace offline se zobrazí chybová zpráva s informacemi o tom, že produkt odpovídající následujícím parametrům nebyl nalezen, ujistěte se, že používáte přepínač `--noweb` s verzí 16.3.5 nebo novější.
>
::: moniker-end

Při instalaci z rozložení, je obsah, který je nainstalován získaných z rozložení. Pokud však vyberete komponentu, která není v rozložení, bude získána z Internetu.  Pokud chcete, aby instalační program sady Visual Studio nestáhl obsah, který ve vašem rozložení chybí, použijte možnost `--noWeb`. Pokud se používá `--noWeb` a v rozložení chybí žádný obsah, který je vybraný k instalaci, instalace se nepovede.

> [!IMPORTANT]
> Možnost `--noWeb` neukončí instalaci sady Visual Studio ze zjišťování aktualizací. Další informace naleznete na stránce [ovládací prvky aktualizace pro síťové nasazení sady Visual Studio](controlling-updates-to-visual-studio-deployments.md) .

### <a name="error-codes"></a>Kódy chyb

Pokud jste použili parametr `--wait` a v závislosti na výsledku operace je proměnná prostředí `%ERRORLEVEL%` nastavená na jednu z následujících hodnot:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Aktualizace rozložení instalace sítě

Jakmile budou aktualizace produktu k dispozici, může být vhodné [Aktualizovat rozložení instalace sítě](update-a-network-installation-of-visual-studio.md) , aby zahrnovalo aktualizované balíčky.

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

Pokud potřebujete vytvořit rozložení pro starší verzi sady Visual Studio, přejít na [https://my.visualstudio.com](https://my.visualstudio.com) a Stáhněte si "opravené" verze spouštěcích prvků sady Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak získat podporu pro offline instalační program

Pokud dochází k potížím s offline instalací chcete vědět o něm. Nejlepším způsobem, jak nás říct, je použití nástroje [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) . Při použití tohoto nástroje můžete nám odeslat telemetrii a protokoly, musíme pomáhají diagnostikovat a opravit problém.

Nabízíme také [**živý chat**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině), který umožňuje problémy související s instalací.

Další možnosti podpory dostupné, máme příliš. Seznam najdete na naší stránce s [názory na zpětnou vazbu](../ide/feedback-options.md) .

## <a name="see-also"></a>Viz také

- [Příručka pro správce sady Visual Studio](visual-studio-administrator-guide.md)
- [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Řešení chyb souvisejících se sítí při instalaci nebo používání sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
- [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
- [Aktualizace sady Visual Studio na standardních hodnotách údržby](update-servicing-baseline.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
