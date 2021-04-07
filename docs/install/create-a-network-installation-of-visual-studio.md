---
title: Vytvoření síťové instalace
description: Naučte se vytvořit bod instalace sítě pro nasazení sady Visual Studio v rámci podniku.
ms.date: 04/06/2021
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
ms.openlocfilehash: 748f0da7810918d8b41247059277fb73158f1bc9
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547424"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Vytvoření síťové instalace sady Visual Studio

Někdy chce správce podniku vytvořit bod instalace sítě, který obsahuje soubory sady Visual Studio, které lze nasadit do klientských pracovních stanic. To usnadňuje scénáře, kdy mohou mít klientské počítače omezená oprávnění nebo omezený přístup k Internetu, nebo když interní týmy chtějí provádět testování kompatibility předtím, než se jejich organizace bude standardizovat na konkrétní verzi sady nástrojů pro vývojáře. Navrhli jsme Visual Studio tak, aby správce mohl _vytvořit rozložení sítě_ , které v podstatě vytváří mezipaměť souborů umístěnou v interní sdílené síťové složce, která zahrnuje všechny soubory sady Visual Studio pro počáteční instalaci a všechny budoucí aktualizace produktů.

 > [!NOTE]
 >  - Pokud máte více edicí sady Visual Studio v rámci podniku (například sady Visual Studio 2019 Professional i Visual Studio 2019 Enterprise), musíte pro každou edici vytvořit samostatnou sdílenou síťovou složku pro instalaci.
 >  - Doporučujeme, abyste se rozhodli, jak chcete, aby klienti obdrželi aktualizace produktu _před tím, než_ provedete počáteční instalaci klienta.  Díky tomu je snazší zajistit správné nastavení možností konfigurace. Mezi vaše volby patří klienti, kteří získají aktualizace z umístění rozložení sítě nebo z Internetu. 
 >  - Původní rozložení instalace sady Visual Studio a všechny následné aktualizace produktu se musí nacházet ve stejném síťovém adresáři, aby bylo zajištěno, že funkce opravy a odinstalace funguje správně. 

## <a name="download-the-visual-studio-bootstrapper"></a>Stažení zaváděcího nástroje sady Visual Studio

Stáhněte si soubor zaváděcího nástroje pro edici sady Visual Studio, kterou chcete. Nezapomeňte zvolit možnost **Uložit** a pak zvolte možnost **Otevřít složku**.

::: moniker range="vs-2017"

Chcete-li získat nejnovější zaváděcí nástroj pro sadu Visual Studio 2017 verze 15,9, navštivte stránku [předchozí verze sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) a Stáhněte jeden z následujících souborů zaváděcího nástroje:

| Edice | Bitmap |
|-------------|-----------------------|
|Visual Studio 2017 Enterprise verze 15,9 | vs_enterprise.exe |
|Visual Studio 2017 Professional verze 15,9 | vs_professional.exe |
|Visual Studio 2017 Build Tools verze 15,9  | vs_buildtools.exe |

Mezi další podporované zaváděcí nástroje patří vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe a vs_testprofessional.exe.

::: moniker-end

::: moniker range="vs-2019"

Začněte stažením zaváděcího nástroje sady Visual Studio 2019 ze [stránky stažení sady Visual](https://visualstudio.microsoft.com/downloads) Studio nebo ze stránky [verze sady Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) pro vaši zvolenou verzi a edici sady Visual Studio.  Instalační program &mdash; nebo bude mít konkrétnější soubor, soubor zaváděcího nástroje &mdash; se bude shodovat s jedním z následujících způsobů:

|Edice | Stáhnout|
|-------------|-----------------------|
|Visual Studio Enterprise | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Mezi další podporované zaváděcí nástroje patří [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)a [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit, jakou verzi je, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přečtěte si téma [čísla sestavení sady Visual Studio a data vydání](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit, jakou verzi je, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přečtěte si téma [verze sady Visual studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Vytvoření offline instalační složky

K dokončení tohoto kroku je nutné připojení k Internetu. 

Otevřete příkazový řádek, přejděte do adresáře, do kterého jste stáhli zaváděcí nástroj, a pomocí parametrů zaváděcího nástroje, jak je definováno v [parametrech příkazového řádku pro instalaci sady Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) , vytvořte a udržujte mezipaměť instalace vaší sítě. Běžné příklady vytváření počátečních rozložení jsou uvedené níže a v [příkladech parametrů příkazového řádku pro instalaci sady Visual Studio](../install/command-line-parameter-examples.md).  

   > [!IMPORTANT]
   > Dokončení počátečního rozložení pro národní prostředí v jednom jazyce vyžaduje přibližně 35 GB místa na disku pro Visual Studio Community a 42 GB pro Visual Studio Enterprise. Další [jazykové národní prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) vyžaduje přibližně polovinu až GB každého z nich. Další informace najdete v části [přizpůsobení rozložení sítě](#customize-the-network-layout) . Je třeba mít na vědomí, že následné aktualizace rozložení se musí taky ukládat do stejného síťového umístění, takže se očekává, že obsah adresáře v umístění rozložení sítě může být v průběhu času poměrně velký.  
   
- Chcete-li vytvořit počáteční rozložení Visual Studio Enterprise se všemi jazyky a všemi funkcemi, spusťte příkaz:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Chcete-li vytvořit počáteční rozložení Visual Studio Professional se všemi jazyky a všemi funkcemi, spusťte příkaz:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Úprava response.jsv souboru

Soubor můžete upravit `response.json` tak, aby se nastavily výchozí hodnoty, které se použijí při spuštění instalačního programu.  Můžete třeba nakonfigurovat `response.json` soubor tak, aby vybral konkrétní sadu úloh, které se mají vybrat automaticky. Můžete také nakonfigurovat, `response.json` aby určovala, jestli má klient přijímat jenom aktualizované soubory z umístění rozložení sítě. Další informace naleznete v tématu [Automatizace instalace sady Visual Studio se souborem odpovědí](../install/automated-installation-with-response-file.md). 

Pokud narazíte na problém s zaváděcím nástrojem sady Visual Studio při párování se souborem dojde k chybě `response.json` , přečtěte si téma [řešení potíží s chybami sítě při instalaci nebo použití stránky sady Visual Studio](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) , kde najdete další informace.

## <a name="copy-the-layout-to-a-network-share"></a>Zkopírování rozložení do síťové sdílené složky

Rozdělte rozložení na sdílenou síťovou složku, aby bylo možné spustit z klientských počítačů.

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

### <a name="save-your-layout-options"></a>Uložení možností rozložení

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

Nejdřív je potřeba pochopit, že existují dva typy spouštěcích prvků sady Visual Studio – jeden, který může být charakterizován slovy "poslední", "Current", "doručoval" a "Tip" a jedním z nich v podstatě znamená "pevná verze". Oba typy souborů zaváděcího nástroje mají přesně stejný název a nejlepším způsobem, jak typ odlišit, je věnovat pozornost tomu, kde jste z nich získali pozornost. Zaváděcí nástroje sady Visual Studio, které jsou k dispozici na [stránce soubory ke stažení pro Visual](https://visualstudio.microsoft.com/downloads) Studio, se považují za doručoval nástroje sady Visual Studio a vždy instalují (nebo aktualizují) nejnovější verzi, která je v kanálu v době spuštění zaváděcího nástroje k dispozici. Zavaděče sady Visual Studio jsou k dispozici na stránce [verze sady Visual studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history) nebo které jsou vložené v rámci aktualizace správce v katalogu Microsoft Update nainstalujte konkrétní opravenou verzi produktu. 

Pokud si tedy stáhnete doručoval zaváděcí nástroj sady Visual Studio ještě dnes a spustíte ho šest měsíců od tohoto okamžiku, nainstaluje se verze sady Visual Studio, která je aktuální v době, kdy je zaváděcí nástroj spuštěn. Je navržena tak, aby vždy instalovala nejnovější bity a udržovala vaše aktuální.

Pokud si stáhnete zaváděcí nástroj pro pevné připojení nebo pokud spustíte aktualizaci správce, kterou jste si stáhli z katalogu Microsoftu, bude vždycky instalovat konkrétní verzi produktu bez ohledu na to, kdy byla spuštěna.

Nakonec můžete vytvořit rozložení sítě pomocí některého z těchto zaváděcích nástroje a verze, která se vytvoří v rozložení, bude záviset na zaváděcím programu, který používáte, například bude to buď pevná verze, nebo aktuální. Pak můžete aktualizovat rozložení sítě pomocí pozdějšího zaváděcího nástroje nebo můžete použít také balíček aktualizace správce z katalogu Microsoft Update. Bez ohledu na to, jak rozložení aktualizujete, bude výsledné aktualizované rozložení mezipamětí balíčku, která obsahuje konkrétní verzi produktu, a pak se bude chovat jako zaváděcí nástroj pevné linky. Takže pokud se klient nainstaluje z rozložení, klient nainstaluje konkrétní verzi sady Visual Studio, která existuje v rozložení (i v případě, že může existovat novější verze online). 

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
