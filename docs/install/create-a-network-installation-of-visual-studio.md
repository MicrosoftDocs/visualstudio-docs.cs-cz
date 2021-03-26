---
title: Vytvoření síťové instalace
description: Naučte se vytvořit bod instalace sítě pro nasazení sady Visual Studio v rámci podniku.
ms.date: 08/27/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e76c5346230b6991f238384a4852938dcc540f6c
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2021
ms.locfileid: "105616932"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Vytvoření síťové instalace sady Visual Studio

Podnikový správce obvykle vytvoří bod instalace sítě pro nasazení do klientských pracovních stanic. Navrhli jsme aplikaci Visual Studio, která vám umožní ukládat soubory do mezipaměti pro počáteční instalaci společně se všemi aktualizacemi produktu do jediné složky. (Tento proces je také označován jako _Vytvoření rozložení_.)

Provedli jsme to tak, aby klientské pracovní stanice mohli používat stejné síťové umístění ke správě instalace i v případě, že se ještě neaktualizovaly na nejnovější aktualizaci údržby.

 > [!NOTE]
 > Pokud máte více edicí sady Visual Studio v rámci podniku (například Visual Studio Professional i Visual Studio Enterprise), musíte pro každou edici vytvořit samostatnou sdílenou síťovou složku pro instalaci.

## <a name="download-the-visual-studio-bootstrapper"></a>Stažení zaváděcího nástroje sady Visual Studio

Stáhněte si soubor zaváděcího nástroje pro edici sady Visual Studio, kterou chcete. Nezapomeňte zvolit možnost **Uložit** a pak zvolte možnost **Otevřít složku**.

::: moniker range="vs-2017"

Další informace o tom, jak to udělat, najdete na stránce pro stažení [předchozích verzí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , kde můžete získat zaváděcí nástroj pro visual Studio 2017.

Instalační program &mdash; nebo bude mít konkrétnější soubor, soubor zaváděcího nástroje &mdash; by se měl shodovat nebo být podobný jednomu z následujících.

| Edice | Bitmap |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Build Tools   | **vs_buildtools.exe** |

Mezi další podporované zaváděcí nástroje patří **vs_feedbackclient.exe**, **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe** a **vs_testprofessional.exe**.

::: moniker-end

::: moniker range="vs-2019"

Instalační program &mdash; nebo bude mít konkrétnější soubor, soubor zaváděcího nástroje &mdash; by se měl shodovat nebo být podobný jednomu z následujících.

|Edice | Stáhnout|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Mezi další podporované zaváděcí nástroje patří [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)a [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přejděte na stránku [čísla sestavení sady Visual Studio a data verzí](visual-studio-build-numbers-and-release-dates.md) .

## <a name="create-an-offline-installation-folder"></a>Vytvoření offline instalační složky

K dokončení tohoto kroku je nutné připojení k Internetu. Chcete-li vytvořit offline instalaci se všemi jazyky a všemi funkcemi, použijte příkaz, který je podobný jednomu z následujících příkladů. Tato složka musí zůstat statická a všechny aktualizace rozložení musí být zahrnuty do této složky. 

   > [!IMPORTANT]
   > Kompletní rozložení pro národní prostředí s jedním jazykem vyžaduje přibližně 35 GB místa na disku pro Visual Studio Community a 42 GB pro Visual Studio Enterprise. Další [jazykové národní prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) vyžaduje přibližně polovinu až GB každého z nich. Další informace najdete v části [přizpůsobení rozložení sítě](#customize-the-network-layout) .
   >
   > [!TIP]
   > Ujistěte se, že jste příkaz spustili z adresáře pro stahování. Obvykle to je `C:\Users\<username>\Downloads` na počítači se systémem Windows 10.

- Pro Visual Studio Enterprise spusťte:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Pro Visual Studio Professional spusťte:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Úprava response.jsv souboru

Úpravou response.jsmůžete nastavit výchozí hodnoty, které se použijí při spuštění instalačního programu.  Můžete třeba nakonfigurovat `response.json` soubor pro výběr konkrétní sady úloh, které se automaticky vybraly. Podrobnosti najdete v tématu [Automatizace instalace sady Visual Studio se souborem odpovědí](automated-installation-with-response-file.md) .

A pokud narazíte na problém s zaváděcím nástrojem sady Visual Studio při párování s response.jsv souboru, přečtěte si část "selhání analýzy ID z nadřazeného procesu" při [řešení potíží souvisejících se sítí při instalaci nebo použití sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) , kde najdete další informace o tom, co dělat.

## <a name="copy-the-layout-to-a-network-share"></a>Zkopírování rozložení do síťové sdílené složky

Rozdělte rozložení na sdílenou síťovou složku, aby ho bylo možné spouštět z jiných počítačů.

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

K přizpůsobení rozložení sítě můžete použít několik možností. Můžete vytvořit částečné rozložení, které obsahuje pouze konkrétní sadu [jazykových prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [zatížení, komponenty a jejich doporučené nebo volitelné závislosti](workload-and-component-ids.md). To může být užitečné, pokud víte, že budete nasazovat pouze podmnožinu úloh do klientských pracovních stanic. Mezi typické parametry příkazového řádku pro přizpůsobení rozložení patří:

* `--add` Chcete-li určit [ID úlohy nebo součásti](workload-and-component-ids.md). <br>Pokud `--add` se použije, stáhnou se jenom ty úlohy a součásti, které jsou určené pro `--add` .  Pokud `--add` se nepoužije, stáhnou se všechny úlohy a součásti.
* `--includeRecommended` zahrnutí všech doporučených součástí pro zadaná ID úloh
* `--includeOptional` pro zahrnutí všech doporučených a volitelných komponent pro zadaná ID úloh.
* `--lang` pro určení [jazykových národních prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Zde je několik příkladů vytvoření vlastního částečného rozložení.

* Chcete-li stáhnout všechny úlohy a součásti pouze pro jeden jazyk, spusťte příkaz:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Chcete-li stáhnout všechny úlohy a součásti pro více jazyků, spusťte příkaz:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Chcete-li stáhnout jednu úlohu pro všechny jazyky, spusťte příkaz:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Ke stažení dvou úloh a jedné volitelné komponenty pro tři jazyky spusťte příkaz:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Stažení dvou úloh a všech doporučených součástí:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Pokud chcete stáhnout dvě úlohy a všechny doporučené a volitelné komponenty, spusťte:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Novinka ve verzi 15,3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Uložení možností rozložení

::: moniker-end

Když spustíte příkaz rozložení, možnosti, které zadáte, se uloží (například úlohy a jazyky). Následné příkazy rozložení budou zahrnovat všechny předchozí možnosti.  Tady je příklad rozložení s jednou úlohou pouze pro angličtinu:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Pokud chcete toto rozložení aktualizovat na novější verzi, nemusíte zadávat žádné další parametry příkazového řádku. Předchozí nastavení se uloží a použijí v dalších příkazech rozložení v této složce rozložení.  V následujícím příkazu se aktualizuje existující částečné rozložení.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Pokud chcete přidat další úlohu, tady je příklad, jak to provést. V tomto případě přidáme úlohu Azure a lokalizovaný jazyk.  V tomto rozložení jsou teď zahrnuté i spravované desktopy i Azure.  Pro všechny tyto úlohy jsou k dispozici jazykové prostředky pro angličtinu a němčinu. Rozložení se aktualizuje na nejnovější dostupnou verzi.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Chcete-li aktualizovat existující rozložení na celé rozložení, použijte možnost--All, jak je znázorněno v následujícím příkladu.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Nasazení z síťové instalace

Správci mohou do klientských pracovních stanic nasadit sadu Visual Studio jako součást instalačního skriptu. Nebo uživatelé, kteří mají práva správce, mohou spustit instalaci přímo ze sdílené složky a nainstalovat aplikaci Visual Studio do svého počítače.

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
> Při spuštění jako součást dávkového souboru, `--wait` možnost zajistí, že `vs_enterprise.exe` proces počká, dokud nebude instalace dokončena, než vrátí ukončovací kód.
>
> To je užitečné v případě, že podnikový správce chce provést další akce při dokončené instalaci (například při [použití kódu Product Key pro úspěšnou instalaci](automatically-apply-product-keys-when-deploying-visual-studio.md)), ale musí počkat na dokončení instalace pro zpracování návratového kódu z této instalace.
>
> Pokud nepoužijete `--wait` , proces se `vs_enterprise.exe` ukončí před dokončením instalace a vrátí nepřesný ukončovací kód, který nepředstavuje stav operace instalace.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> V případě instalace offline se zobrazí chybová zpráva s informacemi o tom, že produkt odpovídající následujícím parametrům nebyl nalezen, ujistěte se, že používáte `--noweb` přepínač s verzí 16.3.5 nebo novější.
>
::: moniker-end

Při instalaci z rozložení je obsah, který se instaluje, získaný z rozložení. Pokud však vyberete komponentu, která není v rozložení, bude získána z Internetu.  Pokud chcete, aby instalační program sady Visual Studio nestáhl obsah, který ve vašem rozložení chybí, použijte `--noWeb` možnost. Pokud `--noWeb` se použije a v rozložení chybí žádný obsah, který je vybraný k instalaci, instalace se nepovede.

> [!TIP]
> Pokud chcete instalovat z offline zdroje na počítači, který není připojen k Internetu, zadejte obě `--noWeb` `--noUpdateInstaller` Možnosti a. Předchozí zabrání stahování aktualizovaných úloh, komponent a tak dále. Druhý postup brání instalačnímu programu v automatických aktualizacích z webu.

> [!IMPORTANT]
> `--noWeb`Možnost neukončí instalaci sady Visual Studio na počítači připojeném k Internetu, aby zkontrolovala aktualizace. Další informace naleznete na stránce [ovládací prvky aktualizace pro síťové nasazení sady Visual Studio](controlling-updates-to-visual-studio-deployments.md) .

### <a name="error-codes"></a>Kódy chyb

Pokud jste použili `--wait` parametr a pak v závislosti na výsledku operace, `%ERRORLEVEL%` Proměnná prostředí je nastavena na jednu z následujících hodnot:

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
> Pokud ale vytvoříte *rozložení* a pak z něho nainstalujete, rozložení nainstaluje konkrétní verzi sady Visual Studio, která existuje v rozložení. I když může existovat novější verze online, získáte verzi sady Visual Studio, která je v rozložení.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Zavaděče sady Visual Studio, které jsou k dispozici na [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads) Stáhněte a nainstalujte nejnovější verzi sady Visual Studio, která je dostupná při každém spuštění.
>
> Pokud si tedy stáhnete Visual Studio *zaváděcí nástroj* ještě dnes a spustíte ho šest měsíců od tohoto okamžiku, nainstaluje se verze sady Visual Studio, která je aktuální v době spuštění zaváděcího nástroje.
>
> Pokud ale vytvoříte *rozložení* a pak z něho nainstalujete, rozložení nainstaluje konkrétní verzi sady Visual Studio, která existuje v rozložení. I když může existovat novější verze online, získáte verzi sady Visual Studio, která je v rozložení.

::: moniker-end

Pokud potřebujete vytvořit rozložení pro starší verzi sady Visual Studio, přejít na adresu [https://my.visualstudio.com](https://my.visualstudio.com) a Stáhněte si "opravené" verze spouštěcích prvků sady Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak získat podporu pro offline instalátor

Pokud dojde k potížím s offline instalací, chceme o něm znát. Nejlepším způsobem, jak nás říct, je použití nástroje [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) . Při použití tohoto nástroje můžete nám poslat telemetrii a protokoly, které potřebujeme, abychom nám mohli pomoct diagnostikovat a vyřešit problém.

Nabízíme také možnost podpory [**instalace**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině) pro problémy související s instalací.

K dispozici jsou i další možnosti podpory. Seznam najdete na naší stránce s [názory na zpětnou vazbu](../ide/feedback-options.md) .

## <a name="see-also"></a>Viz také

- [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
- [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Řešení chyb souvisejících se sítí při instalaci nebo používání sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
- [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
- [Aktualizace sady Visual Studio v servisním směrném plánu](update-servicing-baseline.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
- [Instalace certifikátů vyžadovaných pro instalaci sady Visual Studio offline](install-certificates-for-visual-studio-offline.md)
