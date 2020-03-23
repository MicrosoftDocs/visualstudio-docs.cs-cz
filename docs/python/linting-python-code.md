---
title: Použití kódu PyLint pro Python
description: Spusťte PyLint v sadě Visual Studio a zkontrolujte problémy v kódu Pythonu, včetně možností příkazového řádku pro přizpůsobení linting.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bf503cff7d8de2c00a93385113de05de00059390
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62956801"
---
# <a name="use-pylint-to-check-python-code"></a>Kontrola kódu Pythonu pomocí PyLintu

[PyLint](https://www.pylint.org/), široce používaný nástroj, který kontroluje chyby v kódu Pythonu a podporuje dobré vzory kódování Pythonu, je integrován do Visual Studia pro projekty Pythonu.

## <a name="run-pylint"></a>Spustit PyLint

Stačí kliknout pravým tlačítkem myši na projekt Pythonu v **Průzkumníku řešení** a vybrat **Python** > **Run PyLint**:

![Příkaz PyLint v kontextové nabídce pro projekty Pythonu](media/code-pylint-command.png)

Pomocí tohoto příkazu se zobrazí výzva k instalaci PyLint do aktivního prostředí, pokud ještě není k dispozici.

Upozornění a chyby PyLint se zobrazí v okně **Seznam chyb:**

![Seznam chyb PyLint](media/code-pylint-error-list.png)

Poklepáním na chybu přejdete přímo do zdrojového kódu, který problém vygeneroval.

> [!Tip]
> Podrobný seznam všech výstupních zpráv PyLint naleznete v [odkazu na funkce PyLint.](https://pylint.readthedocs.io/en/latest/technical_reference/features.html)

## <a name="set-pylint-command-line-options"></a>Nastavení voleb příkazového řádku PyLint

Část [možností příkazového řádku](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) v dokumentaci PyLint popisuje, jak řídit chování PyLint prostřednictvím konfiguračního souboru *.pylintrc.* Takový soubor může být umístěn v kořenovém adresáři projektu Pythonu v sadě Visual Studio nebo jinde v závislosti na tom, jak široce chcete, aby se tato nastavení použila (podrobnosti najdete v [tématu možnosti příkazového řádku).](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)

Chcete-li například potlačit upozornění "chybějící docstring" zobrazená na předchozím obrázku se souborem *.pylintrc* v projektu, proveďte kroky:

1. Na příkazovém řádku přejděte do kořenového adresáře projektu (který obsahuje soubor *.pyproj)* a spusťte následující příkaz pro generování konfiguračního souboru s komentáři:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. V Průzkumníkovi řešení sady Visual Studio klepněte pravým tlačítkem myši na projekt, vyberte **přidat** > **existující položku**, přejděte na nový soubor *.pylintrc,* vyberte ho a vyberte **Přidat**.

1. Otevřete soubor pro úpravy, který má několik nastavení, se kterými můžete pracovat. Chcete-li upozornění zakázat, `[MESSAGES CONTROL]` vyhledejte `disable` oddíl a vyhledejte nastavení v této části. Existuje dlouhý řetězec konkrétních zpráv, ke kterým můžete připojit podle toho, co chcete. V příkladu zde `,missing-docstring` připojit (včetně vymezující čárky).

1. Uložte soubor *.pylintrc* a znovu spusťte PyLint, abyste zjistili, že upozornění jsou nyní potlačena.

> [!Tip]
> Chcete-li použít soubor *.pylintrc* ze sdílené síťové `PYLINTRC` složky, vytvořte proměnnou prostředí s názvem s hodnotou názvu souboru ve sdílené síťové složce pomocí cesty UNC nebo mapovaného písmene jednotky. Například, `PYLINTRC=\\myshare\python\.pylintrc`.
