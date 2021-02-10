---
title: Aktualizace síťové instalace
description: Naučte se aktualizovat instalaci sady Visual Studio na základě sítě pomocí příkazu--layout.
ms.date: 06/29/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6829bac79f747d4f9bacfe5e71f57352fcad0970
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959152"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualizace síťové instalace sady Visual Studio

Je možné aktualizovat rozložení instalace sítě sady Visual Studio s nejnovějšími aktualizacemi produktu, aby bylo možné je použít jako bod instalace pro nejnovější aktualizaci sady Visual Studio a také k údržbě instalací, které jsou již nasazeny na klientských pracovních stanicích.

## <a name="how-to-update-a-network-layout"></a>Postup aktualizace rozložení sítě

> [!IMPORTANT]
> V těchto pokynech se předpokládá, že jste dříve vytvořili rozložení instalace sítě. Další informace o tom, jak to udělat, najdete na stránce [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md) .

Chcete-li aktualizovat sdílenou síťovou instalaci tak, aby obsahovala nejnovější aktualizace, spusťte `--layout` příkaz pro přírůstkové stažení aktualizovaných balíčků.

::: moniker range="vs-2017"

**Novinka v 15,3**: Pokud jste při [prvním vytvoření rozložení sítě](create-a-network-installation-of-visual-studio.md)vybrali částečné rozložení, tato nastavení se uloží. Jakékoli budoucí příkazy rozložení používají předchozí možnosti a všechny nové možnosti, které zadáte. Pokud ale používáte rozložení starší verze, měli byste použít stejné parametry příkazového řádku, které jste použili při prvním vytvoření rozložení instalace sítě (jinými slovy, stejné úlohy a jazyky) k aktualizaci jejího obsahu.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste při [prvním vytvoření rozložení sítě](create-a-network-installation-of-visual-studio.md)vybrali částečné rozložení, tato nastavení se uloží. Jakékoli budoucí příkazy rozložení používají předchozí možnosti a všechny nové možnosti, které zadáte.

::: moniker-end

Pokud budete hostovat rozložení sdílené složky, měli byste aktualizovat soukromou kopii rozložení (například c:\VSLayout) a potom po stažení veškerého aktualizovaného obsahu ho zkopírovat do sdílené složky (například \\ server\products\VS). Pokud to neuděláte, je pravděpodobné, že všichni uživatelé, kteří během aktualizace rozložení spouštějí instalaci, nemusí být schopni získat veškerý obsah z rozložení, protože ještě není úplně aktualizovaný.

Pojďme si projít několik příkladů, jak vytvořit a následně aktualizovat rozložení:

* Nejprve tady je příklad, jak vytvořit rozložení s jednou úlohou pouze pro angličtinu:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Zde je postup, jak aktualizovat stejné rozložení na novější verzi. Nemusíte zadávat žádné další parametry příkazového řádku. Předchozí nastavení bylo uloženo a bude použito v dalších příkazech rozložení v této složce rozložení.

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
    > Operace aktualizace neinstaluje nově přidané volitelné součásti. Pokud potřebujete nově přidané volitelné součásti, odeberte staré volitelné komponenty v `Layout.JSON` [souboru odpovědí](automated-installation-with-response-file.md) a součásti, které potřebujete, přidejte do oddílu "Přidat" v tématu `Layout.JSON` . 
    >
    > **Alternativní řešení**: po upgradu pro instalaci chybějících součástí spusťte samostatnou operaci úprav.

* A konečně, jak přidat další úlohu a lokalizovaný jazyk bez aktualizace verze. (Tento příkaz přidá úlohu *vývoje ASP.NET a webu* .)  V tomto rozložení jsou teď součástí spravovaných úloh Desktop, Azure a ASP.NET & Web Development. Pro všechny tyto úlohy jsou k dispozici také jazykové prostředky pro angličtinu, němčinu a francouzštinu.  Při spuštění tohoto příkazu se ale rozložení neaktualizovalo na nejnovější dostupnou verzi. Zůstane v existující verzi.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Nasazení aktualizace klientských počítačů

V závislosti na tom, jak je vaše síťové prostředí nakonfigurované, může být aktualizace nasazená podnikovým správcem nebo iniciovaná z klientského počítače.

* Uživatelé mohou aktualizovat instanci sady Visual Studio, která byla nainstalována z offline instalační složky:
  * Spusťte Instalační program pro Visual Studio.
  * Pak klikněte na **aktualizovat**.

::: moniker range="vs-2017"

* Správci mohou aktualizovat nasazení klientů sady Visual Studio bez jakékoli interakce s uživatelem se dvěma samostatnými příkazy:
  * Nejdřív aktualizujte instalační program sady Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Pak aktualizujte vlastní aplikaci Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Správci mohou aktualizovat nasazení klientů sady Visual Studio bez jakékoli interakce s uživatelem se dvěma samostatnými příkazy:
  * Nejdřív aktualizujte instalační program sady Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Pak aktualizujte vlastní aplikaci Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Pomocí [ příkazuvswhere.exe](tools-for-managing-visual-studio-instances.md) Identifikujte instalační cestu existující instance aplikace Visual Studio v klientském počítači.
>
> [!TIP]
> Podrobnosti o tom, jak řídit, kdy se mají uživatelům zobrazovat oznámení o aktualizacích, najdete v tématu [řízení aktualizací pro nasazení sady Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md).

## <a name="verify-a-layout"></a>Ověření rozložení

Použijte `--verify` k ověření dodané mezipaměti offline. Kontroluje, zda soubory balíčků chybí nebo jsou neplatné. Na konci ověřování se zobrazí seznam chybějících souborů a neplatných souborů.

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

V každé složce "GUID" je uloženo několik souborů. Mezi dva soubory s největším zájmem patří soubor "catalog.json" a soubor "version.txt". Soubor catalog.json je zastaralý manifest katalogu, který budete muset předat `--clean` Možnosti. Druhý version.txt soubor obsahuje verzi tohoto zastaralého manifestu katalogu. Na základě čísla verze se můžete rozhodnout, jestli chcete z tohoto manifestu katalogu odebrat zastaralé balíčky. Stejný postup můžete provést stejně jako ostatní složky "GUID". Po provedení rozhodnutí pro katalogy, které chcete vyčistit, spusťte `--clean` příkaz zadáním cest k souborům do těchto katalogů.

Tady je několik příkladů použití možnosti--Clean:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Můžete také vyvolat vs_enterprise.exe v rámci &lt; layoutDir &gt; . Tady je příklad:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Při spuštění tohoto příkazu provede instalační program analýzu složky offline mezipaměti, aby našel seznam souborů, které se odebere. Pak budete mít možnost zkontrolovat soubory, které se budou odstraňovat, a potvrdit odstranění.

## <a name="get-support-for-your-offline-installer"></a>Získání podpory pro offline instalátor

Pokud dojde k potížím s offline instalací, chceme o něm znát. Nejlepším způsobem, jak nás říct, je použití nástroje [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) . Při použití tohoto nástroje můžete nám poslat telemetrii a protokoly, které potřebujeme, abychom nám mohli pomoct diagnostikovat a vyřešit problém.

Nabízíme také [**živý chat**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině), který umožňuje problémy související s instalací.

K dispozici jsou i další možnosti podpory. Seznam najdete na naší stránce s [názory na zpětnou vazbu](../ide/feedback-options.md) .

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
