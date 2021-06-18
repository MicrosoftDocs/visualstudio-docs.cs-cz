---
title: Aktualizace síťové instalace
description: Zjistěte, jak aktualizovat síťovou instalaci Visual Studio pomocí příkazu --layout.
ms.date: 05/26/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b833551d00f4bd8fb158c848d3bf5b48173e563b
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306654"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualizace síťové instalace sady Visual Studio

Je možné aktualizovat rozložení síťové instalace Visual Studio nejnovějšími aktualizacemi produktů, aby bylo možné ho použít jak jako instalační bod pro nejnovější aktualizaci Visual Studio, tak i k údržbě instalací, které jsou už nasazené na klientských pracovních stanicích.

## <a name="how-to-update-a-network-layout"></a>Postup aktualizace rozložení sítě

> [!IMPORTANT]
> Tyto pokyny předpokládají, že jste už dříve vytvořili rozložení instalace sítě a provedli několik rozhodnutí o tom, jak má klient získat aktualizace. Další informace o tom, jak to provést, najdete na stránce Vytvoření síťové instalace Visual Studio [a](create-a-network-installation-of-visual-studio.md) řízení aktualizací [Visual Studio nasazení.](../install/controlling-updates-to-visual-studio-deployments.md)

Pokud chcete aktualizovat síťovou instalační složku tak, aby zahrnuje nejnovější aktualizace, spusťte bootstrapper pomocí parametru a `--layout` stáhněte aktualizované balíčky.

Pokud jste při prvním vytvoření rozložení sítě vybrali částečné [rozložení,](create-a-network-installation-of-visual-studio.md)uloží se tato nastavení. Všechny budoucí příkazy rozložení používají předchozí možnosti a všechny nové možnosti, které zadáte.

Pokud hostíte rozložení sdílené složky, měli byste aktualizovat privátní kopii rozložení (například c:\VSLayout) a po stažení veškerého aktualizovaného obsahu ji zkopírovat do sdílené složky (například \\ server\products\VS). Pokud to neukončíte, je větší pravděpodobnost, že všichni uživatelé, kteří spustí instalační program během aktualizace rozložení, nebudou moct získat veškerý obsah z rozložení, protože ještě nejsou úplně aktualizovaná.

Pojďme si projít několik příkladů, jak vytvořit a pak aktualizovat rozložení:

* Nejprve tady je příklad, jak vytvořit rozložení s jednou úlohou pouze pro angličtinu:

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Tady je postup aktualizace stejného rozložení na novější verzi. Nemusíte zazadat žádné další parametry příkazového řádku. Předchozí nastavení byla uložena a budou je používat všechny následné příkazy rozložení v této složce rozložení.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Tady je postup, jak bezobslužně aktualizovat rozložení na novější verzi. Operace rozložení spustí proces instalace v novém okně konzoly. Okno je otevřené, aby uživatelé viděli konečný výsledek a souhrn všech chyb, ke kterým mohlo dojít. Pokud provádíte operaci rozložení bezobslužným způsobem (například máte skript, který se pravidelně používá k aktualizaci rozložení na nejnovější verzi), použijte parametr a proces okno automaticky `--passive` zavře.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Tady je postup přidání další úlohy a lokalizovaného jazyka.  (Tento příkaz přidá *úlohu Vývoj pro Azure.)*  Toto rozložení teď zahrnuje Managed Desktop i Azure.  Pro všechny tyto úlohy jsou zahrnuté také jazykové prostředky pro angličtinu a němčinu.  A rozložení se aktualizuje na nejnovější dostupnou verzi.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Operace aktualizace nestáhne ani neinstaluje další volitelné součásti buď do rozložení, nebo do klienta. Pokud potřebujete přidat nebo změnit volitelné součásti, nejprve odeberte staré volitelné součásti ze souboru odpovědí a zahrňte nové součásti, které potřebujete, do části `Layout.JSON` [](automated-installation-with-response-file.md) "přidat" v `Layout.JSON` souboru . Když pak spustíte příkaz update v rozložení, stáhne se do rozložení nově přidané komponenty. 
    >
    > Pokud chcete tyto nové součásti nainstalovat na klientský počítač, nezapomeňte provést tyto tři kroky. Nejprve ověřte, že rozložení obsahuje nové součásti, jak je popsáno výše. Dále aktualizujte klienta na nejnovější bity v rozložení.  Nakonec v klientovi spusťte operaci úpravy, která nainstaluje nové součásti (přidané do rozložení) na klientský počítač.

* A nakonec tady je postup, jak přidat další úlohu a lokalizovaný jazyk bez aktualizace verze. (Tento příkaz přidá *úlohu ASP.NET a vývoje webu.)*  V tomto rozložení jsou teď zahrnuté úlohy Managed Desktop, Azure a ASP.NET & Web Development. Pro všechny tyto úlohy jsou zahrnuty také jazykové prostředky pro angličtinu, němčinu a francouzštinu.  Při spuštění tohoto příkazu však rozložení nebylo aktualizováno na nejnovější dostupnou verzi. Zůstává ve stávající verzi.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Nasazení aktualizace do klientských počítačů

V závislosti na tom, jak je síťové prostředí nakonfigurované, může aktualizaci nasadit podnikový správce nebo iniciovat z klientského počítače.

* Uživatelé mohou aktualizovat instanci Visual Studio nainstalovanou z offline instalační složky:
  * Spusťte Instalační program pro Visual Studio.
  * Pak klikněte na **Aktualizovat.**

::: moniker range="vs-2017"

* Správci můžou aktualizovat nasazení klientů Visual Studio bez zásahu uživatele pomocí dvou samostatných příkazů:
  * Nejprve aktualizujte instalační Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Pak aktualizujte samotnou Visual Studio aplikace: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Správci můžou aktualizovat nasazení klientů Visual Studio bez zásahu uživatele pomocí dvou samostatných příkazů:
  * Nejprve aktualizujte instalační Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Pak aktualizujte samotnou Visual Studio aplikace: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range=">=vs-2022"

* Správci můžou aktualizovat nasazení klientů Visual Studio bez zásahu uživatele pomocí dvou samostatných příkazů:
  * Nejprve aktualizujte instalační Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Pak aktualizujte samotnou Visual Studio aplikace: <br>```vs_enterprise.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Pomocí [vswhere.exe identifikujte](tools-for-managing-visual-studio-instances.md) instalační cestu existující instance nástroje Visual Studio na klientském počítači.
>
> [!TIP]
> Podrobnosti o tom, jak řídit, kdy se mají uživatelům prezentovat oznámení o aktualizacích, najdete v tématu Řízení aktualizací síťových [Visual Studio nasazení.](controlling-updates-to-visual-studio-deployments.md)

## <a name="verify-a-layout"></a>Ověření rozložení

Pomocí `--verify` nástroje proveďte ověření dodané offline mezipaměti. Kontroluje, jestli soubory balíčků chybí nebo jsou neplatné. Na konci ověření vytiskne seznam chybějících souborů a neplatných souborů.

```shell
vs_enterprise.exe --layout <layoutDir> --verify
```

Soubor vs_enterprise.exe vyvolat uvnitř layoutDir.

> [!NOTE]
> Některé důležité soubory metadat, které tato možnost `--verify` potřebuje, musí být v offline mezipaměti rozložení. Pokud tyto soubory metadat chybí, příkaz --verify se nemůže spustit a instalační program zobrazí chybu. Pokud k této chybě dojde, vytvořte nové offline rozložení do jiné složky (nebo do stejné složky mezipaměti offline). Pokud to chcete udělat, spusťte stejný příkaz rozložení, který jste použili k vytvoření počátečního offline rozložení. Například, `vs_enterprise.exe --layout <layoutDir>`.

Microsoft pravidelně dodává aktualizace Visual Studio, takže nové rozložení, které vytvoříte, nemusí být stejné jako počáteční rozložení.

> [!NOTE]
> Ověřování funguje jenom u nejnovější verze konkrétní podverdy Visual Studio. Po vydání nové verze nebude ověření fungovat u starších verzí dílčí verze na úrovni oprav.

## <a name="fix-a-layout"></a>Oprava rozložení

Pomocí `--fix` nástroje proveďte stejné ověření jako a `--verify` také se pokuste zjištěné problémy opravit. Tento proces potřebuje připojení k internetu, proto se před vyvoláním ujistěte, že je váš počítač připojený `--fix` k `--fix` internetu.

```shell
vs_enterprise.exe --layout <layoutDir> --fix
```

Soubor vs_enterprise.exe vyvolat uvnitř layoutDir.

## <a name="remove-older-versions-from-a-layout"></a>Odebrání starších verzí z rozložení

Po provedení aktualizací rozložení offline mezipaměti může složka mezipaměti rozložení obsahovat některé zastaralé balíčky, které už nejnovější Visual Studio mezipaměti. Pomocí možnosti můžete `--clean` odebrat zastaralé balíčky ze složky mezipaměti offline.

K tomu budete potřebovat cesty k souborům manifestů katalogu, které obsahují tyto zastaralé balíčky. Manifesty katalogu najdete ve složce Archivovat v mezipaměti offline rozložení. Uloží se tam při aktualizaci rozložení. Ve složce Archive je jedna nebo více pojmenovaných složek GUID, z nichž každá obsahuje zastaralý manifest katalogu. Počet složek GUID by měl být stejný jako počet aktualizací provedených v offline mezipaměti.

Do každé složky GUID se uloží několik souborů. Nejdůležitějšími dvěma soubory jsou soubor "catalog.json" a soubor "version.txt". Soubor "catalog.json" je zastaralý manifest katalogu, který budete muset předat `--clean` možnosti . Druhý version.txt obsahuje verzi tohoto zastaralého manifestu katalogu. Na základě čísla verze se můžete rozhodnout, jestli chcete odebrat zastaralé balíčky z tohoto manifestu katalogu. Můžete to samé dělat i v ostatních složkách GUID. Po rozhodnutí o katalogech, které chcete vyčistit, spusťte příkaz tak, že do těchto katalogů zadáte cesty `--clean` k souborům.

Tady je několik příkladů použití možnosti --clean:

```shell
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```shell
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Můžete také vyvolat vs_enterprise.exe uvnitř &lt; layoutDir &gt; . Tady je příklad:

```shell
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Když spustíte tento příkaz, instalační program analyzuje složku offline mezipaměti a najde seznam souborů, které odebere. Pak budete mít možnost zkontrolovat soubory, které se mají odstranit, a potvrdit odstranění.

## <a name="get-support-for-your-offline-installer"></a>Získání podpory pro offline instalační program

Pokud máte s offline instalací nějaký problém, chceme se o tom dozvědět. Nejlepší způsob, jak nám to říct, je použít [nástroj Prohlásit](../ide/how-to-report-a-problem-with-visual-studio.md) problém. Když použijete tento nástroj, můžete nám poslat telemetrii a protokoly, které potřebujeme, abychom mohli problém diagnostikovat a opravit.

Nabízíme také možnost [**podpory živého chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině) pro problémy související s instalací.

K dispozici jsou i další možnosti podpory. Seznam najdete na naší stránce [s názory.](../ide/feedback-options.md)

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
