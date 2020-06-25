---
title: Vytvoření projektu AI z existujícího kódu
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 8c0909259291bc5d2db2c4a9c8b87b1a0321d362
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371713"
---
# <a name="create-an-ai-project-from-existing-code"></a>Vytvoření projektu AI z existujícího kódu

Po [instalaci Visual Studio Tools for AI](installation.md)je možné snadno převést existující kód Pythonu do projektu sady Visual Studio.

> [!Important]
> Proces popsaný tady nepřesouvá ani nekopíruje původní zdrojové soubory. Pokud chcete pracovat s kopií, nejprve složku duplikujte.

1. Spusťte Visual Studio a vyberte **soubor > nový > projekt**.

2. V dialogovém okně **Nový projekt** vyhledejte "**nástroje AI**", vyberte šablonu "**ze stávajícího kódu Python**", zadejte název a umístění projektu a vyberte **OK**.

   ![Nový projekt z existujícího kódu, krok 1](media/create-project-existing/new-ai-project.png)

3. V průvodci, který se zobrazí, nastavte cestu k vašemu existujícímu kódu, nastavte filtr pro typy souborů a zadejte všechny cesty pro hledání, které váš projekt vyžaduje, a pak vyberte **OK**. Pokud si nejste jisti, jaké vyhledávací cesty jsou, ponechte toto pole prázdné.

   ![Nový projekt z existujícího kódu, krok 2](media/create-project-existing/azurebatch-newproject.png)

   Pokud je váš stávající kód součástí projektu Azure Machine Learning, zkontrolujte, zda **je složka Azure Machine Learning** , aby byla zajištěna úspěšná konverze důležitých Azure Machine Learning podrobností konfigurace, jako je například účet experimentu, pracovní prostor, který výpočetní kontext, který se má použít, a další.

4. Chcete-li nastavit spouštěcí soubor, vyhledejte soubor v **Průzkumník řešení**, klikněte pravým tlačítkem myši a vyberte možnost **nastavit jako spouštěcí soubor**.

5. Spusťte program stisknutím **klávesy CTRL** + **F5** nebo výběrem možnosti **ladění > spustit bez ladění**.

> [!div class="nextstepaction"]
> [Kurz: práce s Pythonem v aplikaci Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Viz také

- [Ručně identifikovat existující prostředí Pythonu](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
