---
title: Použití PyLint pro kód Pythonu
description: Spusťte PyLint v aplikaci Visual Studio a podívejte se na problémy v kódu Pythonu, včetně možností příkazového řádku pro přizpůsobení linting.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d410fd7575b6f71f272f6924d15249f89aa6ebcc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540098"
---
# <a name="use-pylint-to-check-python-code"></a>Použití PyLint ke kontrole kódu Pythonu

[Pylint](https://www.pylint.org/), široce používaný nástroj, který kontroluje chyby v kódu Pythonu a podporuje dobré vzory kódování v Pythonu, je integrován do sady Visual Studio pro projekty Python.

## <a name="run-pylint"></a>Spustit PyLint

Stačí kliknout pravým tlačítkem na projekt Pythonu v **Průzkumník řešení** a vybrat Pylint spustit v **Pythonu**  >  **Run PyLint**:

![Příkaz PyLint v kontextové nabídce pro projekty v Pythonu](media/code-pylint-command.png)

Pomocí tohoto příkazu se zobrazí výzva k instalaci PyLint do aktivního prostředí, pokud ještě není k dispozici.

PyLint upozornění a chyby se zobrazí v okně **Seznam chyb** :

![Seznam chyb PyLint](media/code-pylint-error-list.png)

Dvojitým kliknutím na chybu přejdete přímo ke zdrojovému kódu, který vygeneroval problém.

> [!Tip]
> Podrobný seznam všech výstupních zpráv PyLint najdete v [referenčních informacích k funkcím Pylint](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) .

## <a name="set-pylint-command-line-options"></a>Nastavení možností příkazového řádku PyLint

Část [Možnosti příkazového řádku](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) v dokumentaci k Pylint popisuje, jak řídit chování Pylint prostřednictvím konfiguračního souboru *. pylintrc* . Takový soubor může být umístěn v kořenovém adresáři projektu v jazyce Python v aplikaci Visual Studio nebo jinde v závislosti na tom, jak rozsáhlá tato nastavení chcete použít (podrobnosti naleznete v [možnostech příkazového řádku](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) ).

Chcete-li například potlačit upozornění "chybějící Docstring" zobrazená na předchozím obrázku se souborem *. pylintrc* v projektu, proveďte následující kroky:

1. Na příkazovém řádku přejděte do kořenového adresáře projektu (který má soubor *. pyproj* ) a spuštěním následujícího příkazu vygenerujte konfigurační soubor s komentářem:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. V aplikaci Visual Studio Průzkumník řešení klikněte pravým tlačítkem myši na projekt, vyberte možnost **Přidat**  >  **existující položku**, přejděte k novému souboru *. pylintrc* , vyberte jej a vyberte možnost **Přidat**.

1. Otevřete soubor pro úpravy, který má několik nastavení, se kterými můžete pracovat. Chcete-li zakázat upozornění, vyhledejte `[MESSAGES CONTROL]` část a pak vyhledejte `disable` nastavení v této části. Existuje dlouhý řetězec konkrétních zpráv, ke kterým můžete přidat všechna upozornění, která chcete. V tomto příkladu přidejte `,missing-docstring` (včetně vymezené čárky).

1. Uložte soubor *. pylintrc* a znovu spusťte Pylint, abyste viděli, že upozornění jsou teď potlačená.

> [!Tip]
> Chcete-li použít soubor *. pylintrc* ze sdílené síťové složky, vytvořte proměnnou prostředí s názvem `PYLINTRC` s hodnotou názvu souboru ve sdílené síťové složce pomocí cesty UNC nebo namapovaného písmena jednotky. Například, `PYLINTRC=\\myshare\python\.pylintrc`.
