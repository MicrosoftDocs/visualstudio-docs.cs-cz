---
title: Odebrat Visual Studio
titleSuffix: ''
description: Přečtěte si, jak zcela odebrat Visual Studio z počítače, krok za krokem.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b26e837ec2c4155c1be0b3639368c4315d2aecd3
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85418922"
---
# <a name="remove-visual-studio"></a>Odebrat Visual Studio

Pokud se setkáte s závažnou chybou a nemůžete opravit nebo odinstalovat sadu Visual Studio, můžete spustit `InstallCleanup.exe` Nástroj pro odebrání instalačních souborů a informací o produktu pro všechny nainstalované instance sady Visual studio 2017 nebo Visual studio 2019.

> [!WARNING]
> Pokud dojde k chybě opravy nebo odinstalace, použijte nástroj nástroji installcleanup **jenom jako poslední** . Tento nástroj může odinstalovat funkce z jiných instalací sady Visual Studio nebo jiných produktů, které může být také nutné opravit nebo přeinstalovat.

## <a name="run-installcleanupexe"></a>Spustit InstallCleanup.exe

V nástroji můžete použít některý z následujících přepínačů příkazového řádku `InstallCleanup.exe` :

| Přepínač | Chování |
| ------ | -------- |
| `-i`   | Tento přepínač je výchozí, pokud žádný jiný přepínač nepředává. Odstraní pouze hlavní instalační adresář a informace o produktu. Tento přepínač použijte, pokud chcete po spuštění nástroje znovu nainstalovat stejnou verzi sady Visual Studio `InstallCleanup.exe` . |
| `-f`   | Tento přepínač odebere hlavní instalační adresář, informace o produktu a většinu dalších funkcí nainstalovaných mimo instalační adresář, které mohou být také sdíleny s jinými instalacemi sady Visual Studio nebo jinými produkty. Tento přepínač použijte, pokud chcete odebrat aplikaci Visual Studio, aniž byste ji chtěli nainstalovat později. |

Tady je postup, jak tento `InstallCleanup.exe` nástroj spustit:

1. Ukončete instalační program sady Visual Studio.
1. Otevřete příkazový řádek správce. K otevření příkazového řádku správce použijte následující postup:
   * Do pole "typ zde k hledání" zadejte **cmd** .
   * Klikněte pravým tlačítkem myši na **příkazový řádek**a pak zvolte **Spustit jako správce**.
1. Zadejte úplnou cestu k `InstallCleanup.exe` nástroji a přidejte přepínač příkazového řádku, který dáváte přednost. Ve výchozím nastavení je cesta nástroje následující. Uvozovky ohraničující příkaz obsahující mezery:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Pokud nemůžete najít `InstallCleanup.exe` pod instalační program pro Visual Studio adresářem, který se vždycky nachází v `%ProgramFiles(x86)%\Microsoft Visual Studio` , tady je postup k dalšímu. Postupujte podle pokynů pro [instalaci sady Visual Studio](install-visual-studio.md). Až se zobrazí obrazovka pro výběr úlohy, zavřete okno a postupujte znovu podle pokynů na této stránce.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](modify-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
