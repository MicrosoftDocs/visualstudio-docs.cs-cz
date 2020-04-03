---
title: Vytvoření projektu AI z existujícího kódu
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 416a3358f6fab1fa106f54a360fc156abc16c6dc
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638629"
---
# <a name="create-an-ai-project-from-existing-code"></a>Vytvoření projektu AI z existujícího kódu

Po instalaci [nástrojů Sady Visual Studio pro umělou přípravu](installation.md)je snadné přenést existující kód Pythonu do projektu sady Visual Studio.

> [!Important]
> Zde popsaný proces nepřesouvá ani nekopíruje původní zdrojové soubory. Pokud chcete pracovat s kopií, nejprve ji duplikujte.

1. Spusťte Visual Studio a vyberte **Soubor > Nový > Project**.

2. V dialogovém okně **Nový projekt** vyhledejte "**Nástroje AI**", vyberte šablonu **" Z existujícího kódu Pythonu**", pojmenujte projekt a pojmenujte a utekněte a vyberte **OK**.

   ![Nový projekt z existujícího kódu, krok 1](media/create-project-existing/new-ai-project.png)

3. V průvodci, který se zobrazí, nastavte cestu k existujícímu kódu, nastavte filtr pro typy souborů a určete všechny cesty hledání, které projekt vyžaduje, a pak vyberte **OK**. Pokud nevíte, jaké jsou vyhledávací cesty, ponechte toto pole prázdné.

   ![Nový projekt z existujícího kódu, krok 2](media/create-project-existing/azurebatch-newproject.png)

   Pokud je váš stávající kód součástí projektu Azure Machine Learning, zkontrolujte **složku Is Azure Machine Learning,** abyste zajistili úspěšný převod důležitých podrobností konfigurace Azure Machine Learning, jako je účet Experimentation, Workspace, které výpočetní kontexty a další.

4. Chcete-li nastavit spouštěcí soubor, vyhledejte jej v **Průzkumníku řešení**, klepněte pravým tlačítkem myši a vyberte **příkaz Nastavit jako spouštěcí soubor**.

5. Spusťte program stisknutím **klávesctrl**+**f5** nebo výběrem **ladění > Spustit bez ladění**.

> [!div class="nextstepaction"]
> [Kurz: Práce s Pythonem v Sadě Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Viz také

- [Ruční identifikace existujícího prostředí Pythonu](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
