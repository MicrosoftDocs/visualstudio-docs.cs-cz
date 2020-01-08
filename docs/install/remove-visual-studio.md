---
title: Odebrání sady Visual Studio
titleSuffix: ''
description: Přečtěte si, jak zcela odebrat Visual Studio z počítače, krok za krokem.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fec652e0089a8baae79b6fa9446249710ea2f40d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594510"
---
# <a name="remove-visual-studio"></a>Odebrání sady Visual Studio

Pokud se setkáte s závažnou chybou a nemůžete opravit nebo odinstalovat sadu Visual Studio, můžete spustit nástroj `InstallCleanup.exe` pro odebrání instalačních souborů a informací o produktu pro všechny nainstalované instance sady Visual Studio 2017 nebo Visual Studio 2019.

> [!WARNING]
> Pokud dojde k chybě opravy nebo odinstalace, použijte nástroj nástroji installcleanup **jenom jako poslední** . Tento nástroj může odinstalovat funkce z jiných instalací sady Visual Studio nebo jiných produktů, které může být také nutné opravit nebo přeinstalovat.

## <a name="run-installcleanupexe"></a>Spusťte nástroji installcleanup. exe.

Pomocí některého z následujících přepínačů příkazového řádku můžete použít nástroj `InstallCleanup.exe`:

| Přepínač | Chování |
| ------ | -------- |
| `-i`   | Tento přepínač je výchozí, pokud žádný jiný přepínač nepředává. Odstraní pouze hlavní instalační adresář a informace o produktu. Tento přepínač použijte, pokud chcete po spuštění nástroje `InstallCleanup.exe` znovu nainstalovat stejnou verzi sady Visual Studio. |
| `-f`   | Tento přepínač odebere hlavní instalační adresář, informace o produktu a většinu dalších funkcí nainstalovaných mimo instalační adresář, které mohou být také sdíleny s jinými instalacemi sady Visual Studio nebo jinými produkty. Tento přepínač použijte, pokud chcete odebrat aplikaci Visual Studio, aniž byste ji chtěli nainstalovat později. |

Tady je postup, jak spustit nástroj `InstallCleanup.exe`:

1. Ukončete instalační program sady Visual Studio.
1. Otevřete příkazový řádek správce. Chcete-li otevřít příkazový řádek správce, postupujte podle těchto kroků:
   * Do pole "typ zde k hledání" zadejte **cmd** .
   * Klikněte pravým tlačítkem myši na **příkazový řádek**a pak zvolte **Spustit jako správce**.
1. Zadejte úplnou cestu k nástroji `InstallCleanup.exe` a přidejte přepínač příkazového řádku, který dáváte přednost. Ve výchozím nastavení je cesta nástroje následující:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > Pokud nemůžete najít `InstallCleanup.exe` v adresáři Instalační program pro Visual Studio, který je vždycky umístěný v `%ProgramFiles(x86)%\Microsoft Visual Studio`, tady je postup pro další. Postupujte podle pokynů pro [instalaci sady Visual Studio](install-visual-studio.md). Až se zobrazí obrazovka pro výběr úlohy, zavřete okno a postupujte znovu podle pokynů na této stránce.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](modify-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
