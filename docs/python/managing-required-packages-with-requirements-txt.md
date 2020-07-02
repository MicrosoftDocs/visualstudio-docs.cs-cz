---
title: Správa závislostí balíčku pomocí souboru requirements.txt
description: requirements.txt soubor popisuje závislosti projektu. Pokud obdržíte projekt, který obsahuje soubor requirements.txt, můžete tyto závislosti snadno nainstalovat v jednom kroku.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9179ca2b77e7a6d3ae5b5dffded06524114a0f8d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544115"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Správa požadovaných balíčků pomocí requirements.txt

Pokud sdílíte projekt s ostatními, použijete systém sestavení nebo naplánujete zkopírovat projekt do jakéhokoli jiného umístění, kde potřebujete obnovit prostředí, je nutné zadat externí balíčky, které projekt vyžaduje. Doporučený postup je použít [souborrequirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), který obsahuje seznam příkazů pro PIP, který nainstaluje požadované verze závislých balíčků. Nejběžnějším příkazem je `pip freeze > requirements.txt` , který zaznamenává aktuální seznam balíčků prostředí do *requirements.txt*.

Technicky, libovolný název souboru může být použit ke sledování požadavků (pomocí `-r <full path to file>` při instalaci balíčku), ale sada Visual Studio poskytuje specifickou podporu pro *requirements.txt*:

- Pokud jste načetli projekt, který obsahuje *requirements.txt* a chcete nainstalovat všechny balíčky uvedené v tomto souboru, rozbalte uzel **prostředí pythonu** v **Průzkumník řešení**, potom klikněte pravým tlačítkem myši na uzel prostředí a vyberte možnost **instalovat z requirements.txt**:

    ![Nainstalovat z requirements.txt](media/environments/environments-requirements-txt-install.png)

- Pokud chcete nainstalovat závislosti ve virtuálním prostředí, vytvořte a aktivujte toto prostředí jako první a pak použijte příkaz **instalovat z requirements.txt** . Další informace o vytvoření virtuálního prostředí najdete v tématu [použití virtuálních](selecting-a-python-environment-for-a-project.md#use-virtual-environments)prostředí.

- Pokud už máte v prostředí nainstalované všechny potřebné balíčky, můžete kliknout pravým tlačítkem na toto prostředí v **Průzkumník řešení** a vybrat **vygenerovat requirements.txt** a vytvořit potřebný soubor. Pokud soubor již existuje, zobrazí se výzva k jeho aktualizaci:

    ![Možnosti aktualizace requirements.txt](media/environments/environments-requirements-txt-replace.png)

  - Možnost **nahradit celý soubor** odebere všechny položky, komentáře a možnosti, které existují.
  - **Aktualizace existujících položek** detekuje požadavky na balíčky a aktualizuje specifikátory verzí tak, aby odpovídaly aktuálně nainstalované verzi.
  - **Aktualizace a přidávání položek aktualizuje** všechny nalezené požadavky a na konec souboru přidá všechny ostatní balíčky.

Vzhledem k tomu, že *requirements.txt* soubory jsou určeny k zablokování požadavků prostředí, všechny nainstalované balíčky jsou vytvořeny s přesnými verzemi. Použití přesných verzí zajišťuje, že můžete prostředí snadno reprodukováno v jiném počítači. Balíčky jsou zahrnuté i v případě, že byly nainstalovány s rozsahem verze, jako se závislostí jiného balíčku nebo s jiným instalačním programem než PIP.

Pokud balíček nejde nainstalovat pomocí PIP a zobrazí se v souboru *requirements.txt* , celá instalace se nezdařila. V takovém případě ručně upravte soubor tak, aby vyloučí tento balíček, nebo použijte [Možnosti PIP](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) a podívejte se na instalovatelný verzi balíčku. Například můžete chtít použít [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) ke kompilaci závislosti a přidat `--find-links <path>` možnost do *requirements.txt*:

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

## <a name="see-also"></a>Viz také:

- [Správa prostředí Pythonu v aplikaci Visual Studio](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Cesty pro hledání](search-paths.md)
- [Referenční dokumentace okna prostředí Pythonu](python-environments-window-tab-reference.md)
