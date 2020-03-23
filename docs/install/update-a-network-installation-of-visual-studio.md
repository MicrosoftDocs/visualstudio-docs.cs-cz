---
title: Aktualizace síťové instalace
description: Zjistěte, jak aktualizovat instalaci sady Visual Studio v síti pomocí příkazu --layout
ms.date: 01/08/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 68acfcd4acc06ff2b370f3d77a30bd4ec21eb6d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114973"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualizace síťové instalace sady Visual Studio

Je možné aktualizovat rozložení instalace sady Visual Studio pomocí nejnovějších aktualizací produktu, aby jej bylo možné použít jako instalační bod pro nejnovější aktualizaci sady Visual Studio a také k údržbě instalací, které jsou již nasazeny do klienta Pracovní stanice.

## <a name="how-to-update-a-network-layout"></a>Jak aktualizovat rozložení sítě

> [!IMPORTANT]
> Tyto pokyny předpokládají, že jste dříve vytvořili rozložení instalace sítě. Další informace o tom, jak to udělat, naleznete na stránce [Vytvoření síťové instalace sady Visual Studio.](create-a-network-installation-of-visual-studio.md)

Chcete-li aktualizovat sdílenou složku instalace sítě tak, aby zahrnovala nejnovější aktualizace, spusťte `--layout` příkaz a postupně stahujte aktualizované balíčky.

::: moniker range="vs-2017"

**Novinka v 15.3**: Pokud jste při [prvním vytvoření rozložení sítě](create-a-network-installation-of-visual-studio.md)vybrali částečné rozložení , budou tato nastavení uložena. Všechny budoucí příkazy rozložení používají předchozí možnosti a všechny nové možnosti, které zadáte. Pokud však používáte rozložení starší verze, měli byste použít stejné parametry příkazového řádku, které jste použili při prvním vytvoření rozložení instalace sítě (jinými slovy stejné úlohy a jazyky) k aktualizaci jeho obsahu.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste při prvním [vytvoření rozložení sítě](create-a-network-installation-of-visual-studio.md)vybrali částečné rozložení , budou tato nastavení uložena. Všechny budoucí příkazy rozložení používají předchozí možnosti a všechny nové možnosti, které zadáte.

::: moniker-end

Pokud hostujete rozložení ve sdílené složce, měli byste aktualizovat soukromou kopii rozložení (například c:\VSLayout) a poté jej po stažení \\veškerého aktualizovaného obsahu zkopírujte do sdílené složky (například server\produkty\VS). Pokud tak neučiníte, je větší pravděpodobnost, že všichni uživatelé, kteří spustí instalační program při aktualizaci rozložení, nemusí být schopni získat veškerý obsah z rozložení, protože ještě není zcela aktualizován.

Pojďme si projít několik příkladů, jak vytvořit a potom aktualizovat rozložení:

* Nejprve je zde příklad, jak vytvořit rozložení pouze s jedním zatížením pro angličtinu:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Zde je návod, jak aktualizovat stejné rozložení na novější verzi. Není nutné zadávat žádné další parametry příkazového řádku. Předchozí nastavení byla uložena a budou použita všemi následujícími příkazy rozložení v této složce rozložení.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Tady je postup, jak bezobslužné nastavení aktualizovat rozvržení na novější verzi. Operace rozložení spustí proces instalace v novém okně konzoly. Okno je ponecháno otevřené, takže uživatelé mohou vidět konečný výsledek a souhrn všech chyb, které mohly nastat. Pokud provádíte operaci rozložení bezobslužným způsobem (například máte skript, který je pravidelně spuštěn aktualizovat rozložení `--passive` na nejnovější verzi), pak použijte parametr a proces automaticky zavře okno.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Tady je postup, jak přidat další úlohu a lokalizovaný jazyk.  (Tento příkaz přidá *úlohu vývoje Azure.)*  Teď jsou v tomto rozložení zahrnuty spravované plochy i Azure.  Jazykové prostředky pro angličtinu a němčinu jsou také zahrnuty pro všechny tyto úlohy.  A rozložení je aktualizováno na nejnovější dostupnou verzi.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Operace aktualizace nenainstaluje nově přidané volitelné součásti, a to ani v případě, že tyto součásti zahrnete do oddílu přidání [souboru odpovědí](automated-installation-with-response-file.md). K tomu dochází, protože operace přidání se nepoužívá během aktualizace.
    >
    > **Řešení:** Po upgradu spusťte samostatnou operaci úprav a nainstalujte chybějící součásti.

* A konečně, tady je návod, jak přidat další úlohy a lokalizovaný jazyk bez aktualizace verze. (Tento příkaz přidá *úlohu ASP.NET a vývoj webových* aplikací.)  Teď spravované desktop, Azure a ASP.NET & web development úlohy jsou zahrnuty v tomto rozložení. Jazykové prostředky pro angličtinu, němčinu a francouzštinu jsou také zahrnuty pro všechny tyto úlohy.  Rozložení však nebylo aktualizováno na nejnovější dostupnou verzi při spuštění tohoto příkazu. Zůstává na stávající verzi.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Nasazení aktualizace do klientských počítačů

V závislosti na konfiguraci síťového prostředí může být aktualizace nasazena správcem rozlehlé sítě nebo iniciována z klientského počítače.

* Uživatelé mohou aktualizovat instanci sady Visual Studio, která byla nainstalována z instalační složky offline:
  * Spusťte Instalační službu sady Visual Studio.
  * Potom klepněte na tlačítko **Aktualizovat**.

::: moniker range="vs-2017"

* Správci mohou aktualizovat klientská nasazení sady Visual Studio bez jakékoli interakce uživatele se dvěma samostatnými příkazy:
  * Nejprve aktualizujte instalační program sady Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Potom aktualizujte samotnou aplikaci Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Správci mohou aktualizovat klientská nasazení sady Visual Studio bez jakékoli interakce uživatele se dvěma samostatnými příkazy:
  * Nejprve aktualizujte instalační program sady Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Potom aktualizujte samotnou aplikaci Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Pomocí [příkazu vswhere.exe](tools-for-managing-visual-studio-instances.md) určete instalační cestu existující instance sady Visual Studio v klientském počítači.
>
> [!TIP]
> Podrobnosti o tom, jak řídit, kdy jsou uživatelům prezentována oznámení o aktualizaci, naleznete [v tématu Řízení aktualizací nasazení sady Visual Studio založených na síti](controlling-updates-to-visual-studio-deployments.md).

## <a name="verify-a-layout"></a>Ověření rozložení

Slouží `--verify` k ověření na dodané mezipaměti offline. Zkontroluje, zda soubory balíčků chybí nebo jsou neplatné. Na konci ověření vytiskne seznam chybějících souborů a neplatných souborů.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe lze vyvolat uvnitř layoutDir.

> [!NOTE]
> Některé důležité soubory metadat, které `--verify` jsou potřebné pro tuto možnost, musí být v mezipaměti rozložení offline. Pokud tyto soubory metadat chybí, "--verify" nelze spustit a instalační program poskytuje chybu. Pokud k této chybě dojde, znovu vytvořte nové offline rozložení do jiné složky (nebo do stejné složky mezipaměti offline. Chcete-li tak učinit, spusťte stejný příkaz rozložení, který jste použili k vytvoření počátečního offline rozložení. Například, `vs_enterprise.exe --layout <layoutDir>`.

Společnost Microsoft dodává aktualizace sady Visual Studio pravidelně, takže nové rozložení, které vytvoříte, nemusí být stejná verze jako počáteční rozložení.

> [!NOTE]
> Ověření funguje pouze pro nejnovější verzi konkrétní dílčí verze sady Visual Studio. Jakmile bude vydána nová verze, ověření nebude fungovat pro dřívější verze stejné dílčí verze na úrovni opravy.

## <a name="fix-a-layout"></a>Oprava rozložení

Slouží `--fix` k provedení stejného ověření jako `--verify` a také se pokuste opravit zjištěné problémy. Tento `--fix` proces potřebuje připojení k internetu, takže se ujistěte, `--fix`že je počítač připojen k internetu, než vyvoláte .

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

vs_enterprise.exe lze vyvolat uvnitř layoutDir.

## <a name="remove-older-versions-from-a-layout"></a>Odebrání starších verzí z rozložení

Po provedení aktualizací rozložení do mezipaměti offline může mít složka mezipaměti rozložení některé zastaralé balíčky, které nejnovější instalace sady Visual Studio již nepotřebujete. Tuto možnost `--clean` můžete použít k odebrání zastaralých balíčků ze složky mezipaměti offline.

Chcete-li to provést, budete potřebovat cesty k souborům do manifestu katalogu, které obsahují tyto zastaralé balíčky. Manifesty katalogu najdete ve složce Archiv v mezipaměti offline rozložení. Jsou tam uloženy při aktualizaci rozložení. Ve složce "Archiv" je jedna nebo více složek s názvem "GUID", z nichž každá obsahuje zastaralý manifest katalogu. Počet složek "GUID" by měl být stejný jako počet aktualizací provedených v offline mezipaměti.

Několik souborů je uloženo uvnitř každé složky "GUID". Dva soubory, které jsou nejvíce zajímavé, jsou soubor "catalog.json" a soubor "version.txt". Soubor "catalog.json" je zastaralý manifest katalogu, který `--clean` budete muset předat možnosti. Druhý soubor version.txt obsahuje verzi tohoto zastaralého manifestu katalogu. Na základě čísla verze se můžete rozhodnout, zda chcete odebrat zastaralé balíčky z tohoto manifestu katalogu. Můžete udělat totéž, jak jdete přes ostatní složky "GUID". Po rozhodnutí o katalogu(s), který chcete vyčistit, `--clean` spusťte příkaz zadáním cesty souborů do těchto katalogů.

Zde je několik příkladů použití možnosti --clean:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Můžete také vyvolat vs_enterprise.exe &lt;uvnitř&gt;layoutDir . Tady je příklad:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Při spuštění tohoto příkazu instalační program analyzuje složku mezipaměti offline a vyhledá seznam souborů, které odebere. Poté budete mít možnost zkontrolovat soubory, které budou odstraněny, a potvrdit odstranění.

## <a name="get-support-for-your-offline-installer"></a>Získejte podporu pro offline instalátor

Pokud narazíte na problém s offline instalací, chceme o něm vědět. Nejlepší způsob, jak nám to říct, je použít nástroj [Nahlásit problém.](../ide/how-to-report-a-problem-with-visual-studio.md) Při použití tohoto nástroje nám můžete poslat telemetrii a protokoly, které potřebujeme, aby nám pomohli diagnostikovat a opravit problém.

Nabízíme také možnost podpory [**živého chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (pouze v angličtině) pro problémy související s instalací.

Máme k dispozici i další možnosti podpory. Seznam najdete na stránce [Zpětná vazba.](../ide/feedback-options.md)

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Průvodce správcem sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Řízení aktualizací nasazení sady Visual Studio v síti](controlling-updates-to-visual-studio-deployments.md)
* [Životní cyklus produktu Visual Studio a servis](/visualstudio/releases/2019/servicing/)
