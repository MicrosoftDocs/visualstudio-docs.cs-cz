---
title: Aktualizace síťové instalace
description: Zjistěte, jak aktualizovat síťové instalace sady Visual Studio pomocí příkazu--rozložení
ms.date: 10/07/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2157a6142f95b6ffe34503a8ee80419fcb9ca506
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018821"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualizace síťové instalace sady Visual Studio

Je možné k aktualizaci rozložení síťové instalace sady Visual Studio s nejnovějšími aktualizacemi tak, aby ji bylo možné použil jako umístění instalace pro nejnovější aktualizaci sady Visual Studio a také k údržbě instalace, které jsou už nasazené do klienta pracovní stanice.

## <a name="how-to-update-a-network-layout"></a>Jak aktualizovat síťový diagram

Pokud chcete sdílenou síťovou instalaci aktualizovat tak, aby obsahovala nejnovější aktualizace, spusťte příkaz `--layout` a postupně stáhněte aktualizované balíčky.

::: moniker range="vs-2017"

**Novinka v 15,3**: Pokud jste vybrali částečné rozložení, při prvním vytvoření rozložení sítě, se uloží. Všechny příkazy budoucí rozložení použít předchozí možnosti plus všechny nové možnosti, které zadáte. Pokud ale používáte rozložení starší verze, měli byste použít stejné parametry příkazového řádku, které jste použili při prvním vytvoření rozložení instalace sítě (jinými slovy, stejné úlohy a jazyky) k aktualizaci jejího obsahu.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste vybrali částečné rozložení, při prvním vytvoření rozložení sítě, se uloží. Všechny příkazy budoucí rozložení použít předchozí možnosti plus všechny nové možnosti, které zadáte.

::: moniker-end

Pokud hostete rozložení sdílené složky, měli byste aktualizovat soukromou kopii rozložení (například c:\VSLayout) a potom po stažení veškerého aktualizovaného obsahu ho zkopírovat do sdílené složky (například \\Server \ Products \ VS). Pokud to neuděláte, existuje větší riziko, že všichni uživatelé, kteří spusťte instalační program, když aktualizujete rozložení nebudou moct získat veškerý obsah z rozložení, protože není dosud aktualizovat úplně.

Pojďme si projít několik příkladů, jak vytvořit a následně aktualizovat rozložení:

* Nejprve tady je příklad toho, jak vytvořit rozložení se sadou jeden pro angličtinu pouze:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Tady je postup k aktualizaci této stejné rozložení na novější verzi. Není nutné specifikovat žádné další parametry příkazového řádku. Předchozí nastavení, které se uložily a budou používat všechny následné rozložení příkazy v této složce rozložení.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Tady je postup k aktualizaci rozložení v bezobslužném na novější verzi. Operace rozložení spustí proces instalace v novém okně konzoly. V okně je otevřená, takže uživatelé uvidí na konečný výsledek a souhrnné informace o chybách, které mohly nastat. Pokud provádíte operaci rozložení v bezobslužném (například máte skript, který se spouští pravidelně aktualizovat na nejnovější verzi rozložení), použije `--passive` parametr a proces se automaticky zavře okno.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Tady je postup pro přidání dalšímu zatížení a lokalizovaný jazyk.  (Tento příkaz přidá úlohu *vývoj pro Azure* .)  Teď Managed Desktop i Azure jsou zahrnuté v tomto rozvržení.  Jazykové prostředky pro angličtinu a němčina jsou také zahrnuté pro všechny tyto úlohy.  A rozložení se aktualizuje na nejnovější dostupnou verzi.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Operace aktualizace neinstaluje nově přidané volitelné součásti, i když tyto součásti zahrnete do oddílu "Přidání" v [souboru odpovědí](automated-installation-with-response-file.md). K tomu dochází, protože se během aktualizace nepoužívá operace přidání.
    >
    > **Alternativní řešení**: Po upgradu na instalaci chybějících součástí spusťte samostatnou operaci úprav.

* A konečně, tady je postup přidejte další úlohy a lokalizovaných bez aktualizace na verzi. (Tento příkaz přidá úlohu *vývoje ASP.NET a webu* .)  V tomto rozložení jsou teď součástí spravovaných úloh Desktop, Azure a ASP.NET & Web Development. Jazykové prostředky pro angličtinu, němčinu a francouzštinu jsou také zahrnuté pro všechny tyto úlohy.  Rozložení však nebyl aktualizován na nejnovější dostupnou verzi, při spuštění tohoto příkazu. Zůstane na existující verze.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="how-to-deploy-an-update-to-client-machines"></a>Jak nasadit aktualizace do klientských počítačů

V závislosti na konfiguraci vašeho síťového prostředí aktualizace buď dá nasadit pomocí Správce rozlehlé sítě nebo zahájeno z klientského počítače.

* Uživatelé můžou aktualizovat instance sady Visual Studio, která byla nainstalována ze složky offline instalace:
  * Spusťte instalační program sady Visual Studio.
  * Potom klikněte na **aktualizace**.

::: moniker range="vs-2017"

* Správci mohou aktualizovat klienta nasazení sady Visual Studio bez nutnosti zásahu uživatele pomocí dvou samostatných příkazů:
  * Nejprve aktualizace instalačního programu sady Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Potom aktualizujte vlastní aplikace Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Správci mohou aktualizovat klienta nasazení sady Visual Studio bez nutnosti zásahu uživatele pomocí dvou samostatných příkazů:
  * Nejprve aktualizace instalačního programu sady Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Potom aktualizujte vlastní aplikace Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Použití [vswhere.exe příkaz](tools-for-managing-visual-studio-instances.md) k identifikaci cesta pro instalaci stávající instance sady Visual Studio na klientském počítači.
>
> [!TIP]
> Podrobnosti o tom, jak řídit, když se zobrazí oznámení o aktualizacích pro uživatele najdete v tématu [řízení aktualizací nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md).

## <a name="how-to-verify-a-layout"></a>Postup ověření rozložení

Použití `--verify` k provedení ověření v offline mezipaměti zadaný. Zkontroluje, jestli jsou soubory balíčků chybí nebo jsou neplatné. Na konci ověření vytiskne seznam chybějících souborů a souborů neplatný.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

Může být vyvolána vs_enterprise.exe uvnitř layoutDir.

> [!NOTE]
> Některé soubory důležitá metadata, které jsou vyžadované `--verify` možnost musí být v mezipaměti offline rozložení. Pokud tyto soubory metadat chybí, "– ověření" nelze spustit, a nabídne instalační program k chybě. Pokud k této chybě dochází, znovu vytvořte nové offline rozložení do jiné složky (nebo do stejné složky, offline mezipaměti. Provedete to tak, spusťte stejný příkaz rozložení, který jste použili k vytvoření počáteční offline rozložení. Například `vs_enterprise.exe --layout <layoutDir>`.

Microsoft pravidelně, dodává aktualizace sady Visual Studio tak nové rozložení, který vytvoříte nemusí mít stejnou verzi jako počáteční rozložení.

> [!NOTE]
> Ověřování funguje pouze pro nejnovější verzi konkrétní dílčí verze sady Visual Studio. Jakmile se uvolní nová verze, ověřování nebude fungovat pro předchozí verze na úrovni opravy stejné dílčí verze.

## <a name="how-to-fix-a-layout"></a>K vyřešení rozložení

Použití `--fix` se provede ověření stejné jako `--verify` a také se pokusí opravit zjištěné problémy. Proces `--fix` potřebuje připojení k Internetu, proto se před vyvoláním `--fix` Ujistěte, že je počítač připojený k Internetu.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

Může být vyvolána vs_enterprise.exe uvnitř layoutDir.

## <a name="how-to-remove-older-versions-from-a-layout"></a>Postup odebrání starších verzí z rozložení

Po provedení aktualizací rozložení pro offline mezipaměť rozložení složky mezipaměti může mít některé zastaralé balíčky, které už nejsou potřeba nejnovější instalace sady Visual Studio. Můžete použít `--clean` možnost odebrat zastaralé balíčky ze složky offline mezipaměti.

K tomuto účelu bude nutné cesty souboru k katalogu manifest(s), které obsahují tyto zastaralé balíčky. Můžete najít že v katalogu manifesty ve složce "Archivu" v mezipaměti offline rozložení. Jsou ukládána došlo při aktualizaci rozložení. Ve složce ", archivu" je jeden nebo více "GUID" s názvem složky, z nichž každý obsahuje manifest zastaralé katalogu. Počet složek "GUID" by měl být stejný jako počet aktualizace provedené v offline mezipaměti.

Několik souborů jsou uloženy v každé složky "GUID". Dva soubory, které vás zajímají nejvíce, se soubor "catalog.json" a "version.txt" soubor. Soubor "catalog.json" je zastaralá katalogu manifestu bude nutné předat `--clean` možnost. Další version.txt soubor obsahuje verzi manifestu zastaralé katalogu. Podle čísla verze, můžete rozhodnout, jestli byste chtěli odebrat zastaralé balíčky z tohoto katalogu manifestu. Můžete provést stejný při procházení další složky "GUID". Po provedení rozhodnutí v katalogy chcete vyčistit, spusťte `--clean` příkaz zadáním cesty souborů tyto katalogů.

Tady je několik příkladů toho, jak použít možnost--vyčistit:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Můžete také vyvolat vs_enterprise.exe uvnitř &lt;layoutDir&gt;. Tady je příklad:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Při spuštění tohoto příkazu analyzuje instalaci složky offline mezipaměti k nalezení seznamu souborů, které se odeberou. Potom budete mít příležitost zkontrolovat soubory, které se chystáte odstranit a potvrďte odstranění.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Řízení aktualizací nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
