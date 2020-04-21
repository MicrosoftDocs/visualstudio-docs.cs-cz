---
title: Odebrat Visual Studio
titleSuffix: ''
description: Přečtěte si, jak aplikaci Visual Studio z počítače odebrat krok za krokem.
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
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 98886df1c7fb09fa30d5c54abe19452780195b6a
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649196"
---
# <a name="remove-visual-studio"></a>Odebrat Visual Studio

Pokud dojde ke katastrofické chybě a nelze opravit nebo odinstalovat `InstallCleanup.exe` Visual Studio, můžete spustit nástroj odebrat instalační soubory a informace o produktu pro všechny nainstalované instance Visual Studio 2017 nebo Visual Studio 2019.

> [!WARNING]
> Nástroj InstallCleanup používejte **pouze jako poslední možnost,** pokud oprava nebo odinstalace selže. Tento nástroj může odinstalovat funkce z jiných instalací sady Visual Studio nebo jiných produktů, které pak může být také nutné opravit nebo přeinstalovat.

## <a name="run-installcleanupexe"></a>Spuštění programu InstallCleanup.exe

S nástrojem můžete použít některý z následujících přepínačů příkazového `InstallCleanup.exe` řádku:

| Přepínač | Chování |
| ------ | -------- |
| `-i`   | Tento přepínač je výchozí, pokud není předán žádný jiný přepínač. Odebere pouze hlavní instalační adresář a informace o produktu. Tento přepínač použijte, pokud chcete po spuštění `InstallCleanup.exe` nástroje přeinstalovat stejnou verzi sady Visual Studio. |
| `-f`   | Tento přepínač odebere hlavní instalační adresář, informace o produktu a většinu dalších funkcí nainstalovaných mimo instalační adresář, které mohou být také sdíleny s jinými instalacemi sady Visual Studio nebo jinými produkty. Tento přepínač použijte, pokud chcete aplikaci Visual Studio odebrat, aniž byste ji později znovu nainstalovali. |

Nástroj spustíte takto: `InstallCleanup.exe`

1. Ukončete instalační program sady Visual Studio.
1. Otevřete příkazový řádek správce. Chcete-li otevřít příkazový řádek správce, postupujte takto:
   * Do pole "Zadejte zde pro vyhledávání" zadejte **cmd.**
   * Klepněte pravým tlačítkem myši na **příkazový řádek**a pak zvolte **Spustit jako správce**.
1. Zadejte úplnou `InstallCleanup.exe` cestu nástroje a přidejte přepínač příkazového řádku, který dáváte přednost. Ve výchozím nastavení je cesta nástroje následující. Dvojité uvozovky uzavírají příkaz obsahující mezery:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Pokud nemůžete najít `InstallCleanup.exe` v adresáři Instalační služby sady Visual `%ProgramFiles(x86)%\Microsoft Visual Studio`Studio, který je vždy umístěn na , tady je co dělat dál. Podle pokynů [nainstalujte visual studio](install-visual-studio.md). Potom při zobrazení obrazovky výběru pracovního vytížení zavřete okno a postupujte podle kroků na této stránce znovu.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](modify-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
