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
ms.openlocfilehash: 74464aa76c24a798d33fa7639cdd0b6a07489bf7
ms.sourcegitcommit: 62e39ea1bf0ed939376c4375fc180ff7c4c760fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2021
ms.locfileid: "110660218"
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

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Tady je postup aktualizace stejného rozložení na novější verzi. Nemusíte zazadat žádné další parametry příkazového řádku. Předchozí nastavení byla uložena a budou je používat všechny následné příkazy rozložení v této složce rozložení.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Tady je postup bezobslužné aktualizace rozložení na novější verzi. Operace rozložení spouští proces instalace v novém okně konzoly. Okno zůstane otevřené, aby si uživatelé mohli zobrazit konečný výsledek a souhrn všech chyb, ke kterým mohlo dojít. Provádíte-li operaci rozložení bezobslužným způsobem (například máte skript, který se pravidelně spouští k aktualizaci vašeho rozložení na nejnovější verzi), pak použijte `--passive` parametr a proces automaticky zavře okno.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Tady je postup, jak přidat další úlohu a lokalizovaný jazyk.  (Tento příkaz přidá úlohu *vývoj pro Azure* .)  V tomto rozložení jsou teď zahrnuté i spravované desktopy i Azure.  K dispozici jsou také jazykové prostředky pro angličtinu a němčinu pro všechny tyto úlohy.  A rozložení se aktualizuje na nejnovější dostupnou verzi.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Operace aktualizace nestáhne ani nenainstaluje další volitelné součásti buď do rozložení, nebo do klienta. Pokud potřebujete přidat nebo změnit volitelné součásti, odeberte nejprve staré volitelné komponenty ze `Layout.JSON` [souboru odpovědí](automated-installation-with-response-file.md) a v části Přidat přidejte nové součásti, které potřebujete `Layout.JSON` . Po spuštění příkazu aktualizovat v rozložení se pak stáhnou nově přidané komponenty do rozložení. 
    >
    > Pokud chcete tyto nové komponenty nainstalovat na klientský počítač, ujistěte se, že provádíte tyto tři kroky. Nejprve ověřte, zda rozložení obsahuje nové komponenty, jak je popsáno výše. Dále aktualizujte klienta na nejnovější bity v rozložení.  Nakonec v klientovi znovu spusťte operaci úprav, která nainstaluje nové součásti (přidané do rozložení) do klientského počítače.

* A konečně, jak přidat další úlohu a lokalizovaný jazyk bez aktualizace verze. (Tento příkaz přidá úlohu *vývoje ASP.NET a webu* .)  V tomto rozložení jsou teď součástí spravovaných úloh Desktop, Azure a ASP.NET & Web Development. Pro všechny tyto úlohy jsou zahrnuty také jazykové prostředky pro angličtinu, němčinu a francouzštinu.  Při spuštění tohoto příkazu však rozložení nebylo aktualizováno na nejnovější dostupnou verzi. Zůstává ve stávající verzi.

  ```cmd
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

> [!NOTE]
> Pomocí [vswhere.exe identifikujte](tools-for-managing-visual-studio-instances.md) instalační cestu existující instance nástroje Visual Studio na klientském počítači.
>
> [!TIP]
> Podrobnosti o tom, jak řídit, kdy se mají uživatelům prezentovat oznámení o aktualizacích, najdete v tématu Řízení aktualizací síťových [Visual Studio nasazení.](controlling-updates-to-visual-studio-deployments.md)

## <a name="verify-a-layout"></a>Ověření rozložení

Pomocí `--verify` nástroje proveďte ověření dodané offline mezipaměti. Kontroluje, jestli soubory balíčků chybí nebo jsou neplatné. Na konci ověření vytiskne seznam chybějících souborů a neplatných souborů.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe lze vyvolat v rámci layoutDir.

> [!NOTE]
> Některé důležité soubory metadat, které jsou potřeba pro `--verify` možnost, musí být v mezipaměti rozložení offline. Pokud tyto soubory metadat chybí, nelze spustit "--ověřit" a instalační program vám zobrazí chybu. Pokud se zobrazí tato chyba, znovu vytvořte nové offline rozložení do jiné složky (nebo do stejné složky offline mezipaměti). Chcete-li tak učinit, spusťte stejný příkaz rozložení, který jste použili k vytvoření počátečního offline rozložení. Například, `vs_enterprise.exe --layout <layoutDir>`.

Společnost Microsoft dodává aktualizace sady Visual Studio pravidelně, takže nové rozložení, které vytvoříte, nemusí mít stejnou verzi jako počáteční rozložení.

> [!NOTE]
> Ověřování funguje pouze pro nejnovější verzi konkrétní dílčí verze sady Visual Studio. Jakmile se uvolní nová verze, ověřování nebude fungovat pro předchozí verze na úrovni opravy stejné dílčí verze.

## <a name="fix-a-layout"></a>Oprava rozložení

Použijte `--fix` k provedení stejného ověření jako `--verify` a také zkuste opravit zjištěné problémy. `--fix`Proces potřebuje připojení k Internetu, proto zkontrolujte, že je váš počítač připojený k Internetu, než ho vyvoláte `--fix` .

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

vs_enterprise.exe lze vyvolat v rámci layoutDir.

## <a name="remove-older-versions-from-a-layout"></a>Odebrání starších verzí z rozložení

Po provedení aktualizací rozložení do offline mezipaměti může složka mezipaměti rozložení obsahovat několik zastaralých balíčků, které už nepotřebuje nejnovější instalace sady Visual Studio. Pomocí této možnosti můžete `--clean` Odebrat zastaralé balíčky ze složky offline cache.

K tomu budete potřebovat cesty k souboru pro manifesty katalogu, které obsahují tyto zastaralé balíčky. Manifesty katalogu můžete najít ve složce archivu v mezipaměti offline rozložení. Při aktualizaci rozložení se uloží. Ve složce Archive existuje jedna nebo více pojmenovaných složek "GUID", z nichž každý obsahuje zastaralý manifest katalogu. Počet složek "GUID" by měl být stejný jako počet aktualizací provedených v offline mezipaměti.

Do každé složky GUID se uloží několik souborů. Nejdůležitějšími dvěma soubory jsou soubor "catalog.json" a soubor "version.txt". Soubor "catalog.json" je zastaralý manifest katalogu, který budete muset předat `--clean` možnosti . Druhý version.txt obsahuje verzi tohoto zastaralého manifestu katalogu. Na základě čísla verze se můžete rozhodnout, jestli chcete odebrat zastaralé balíčky z tohoto manifestu katalogu. Můžete to samé dělat i v ostatních složkách GUID. Po rozhodnutí o katalogech, které chcete vyčistit, spusťte příkaz tak, že do těchto katalogů zadáte cesty `--clean` k souborům.

Tady je několik příkladů použití možnosti --clean:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Můžete také vyvolat vs_enterprise.exe uvnitř &lt; layoutDir &gt; . Tady je příklad:

```cmd
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
* [Řízení aktualizací síťových nasazení Visual Studio nasazení](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio životního cyklu a údržby produktů](/visualstudio/releases/2019/servicing/)
