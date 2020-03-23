---
title: Správa závislostí balíčků pomocí souboru requirements.txt
description: Soubor requirements.txt popisuje závislosti projektu. Pokud obdržíte projekt, který obsahuje soubor requirements.txt, můžete tyto závislosti snadno nainstalovat v jednom kroku.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a1853df63354801ebf0413d3c8707135cb9bb800
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62535702"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Správa požadovaných balíčků pomocí souboru requirements.txt

Pokud sdílíte projekt s ostatními, použijte systém sestavení nebo plánujete zkopírovat projekt do jiného umístění, kde potřebujete obnovit prostředí, je třeba zadat externí balíčky, které projekt vyžaduje. Doporučeným postupem je použití [souboru requirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), který obsahuje seznam příkazů pro pip, který nainstaluje požadované verze závislých balíčků. Nejběžnější majek je `pip freeze > requirements.txt`, který zaznamenává aktuální seznam balíčků prostředí do *souboru requirements.txt*.

Technicky lze ke sledování požadavků (při `-r <full path to file>` instalaci balíčku) použít libovolný název souboru, ale sada Visual Studio poskytuje specifickou podporu pro soubor *requirements.txt*:

- Pokud jste načetli projekt, který obsahuje *soubor requirements.txt* a chcete nainstalovat všechny balíčky uvedené v tomto souboru, rozbalte uzel **Prostředí Pythonu** v **Průzkumníku řešení**, klepněte pravým tlačítkem myši na uzel prostředí a vyberte instalovat z **souboru requirements.txt**:

    ![Instalace z souboru requirements.txt](media/environments/environments-requirements-txt-install.png)

- Pokud chcete nainstalovat závislosti ve virtuálním prostředí, nejprve vytvořte a aktivujte toto prostředí a pak použijte příkaz **Instalovat z souboru requirements.txt.** Další informace o vytváření virtuálního prostředí naleznete v tématu [Použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Pokud již máte všechny potřebné balíčky nainstalované v prostředí, můžete na toto prostředí klepnout pravým tlačítkem myši v **Průzkumníkovi řešení** a vybrat **soubor Generate requirements.txt** a vytvořit potřebný soubor. Pokud soubor již existuje, zobrazí se výzva, jak jej aktualizovat:

    ![Aktualizovat možnosti requirements.txt](media/environments/environments-requirements-txt-replace.png)

  - **Nahradit celý soubor** odstraní všechny položky, komentáře a možnosti, které existují.
  - **Aktualizace existujících položek** zjistí požadavky na balíček a aktualizuje specifikátory verze tak, aby odpovídaly aktuálně nainstalované verzi.
  - **Aktualizace a přidání položek** aktualizuje všechny nalezené požadavky a přidá všechny ostatní balíčky na konec souboru.

Vzhledem k tomu, že soubory *requirements.txt* jsou určeny ke zmrazení požadavků prostředí, jsou všechny nainstalované balíčky napsány s přesnými verzemi. Použití přesných verzí zajišťuje, že můžete snadno reprodukovat vaše prostředí v jiném počítači. Balíčky jsou zahrnuty i v případě, že byly nainstalovány s rozsahem verzí, jako závislost jiného balíčku nebo s instalačním programem jiným než pip.

Pokud balíček nelze nainstalovat pomocí pipu a zobrazí se v souboru *requirements.txt,* celá instalace se nezdaří. V takovém případě ručně upravte soubor tak, aby byl tento balíček vyloučen, nebo použijte [možnosti pipu](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) k odkazování na instalovatelnou verzi balíčku. Můžete například raději použít [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) ke kompilaci závislosti `--find-links <path>` a přidat možnost *na adresu requirements.txt*:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu v sadě Visual Studio](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Cesty pro hledání](search-paths.md)
- [Odkaz na okno prostředí Pythonu](python-environments-window-tab-reference.md)
