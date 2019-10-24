---
title: Vytvoření projektu AI z existujícího kódu
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 0981a276a21e1b3f816c6a182df29f1c4adb0d1c
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777445"
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

   Pokud je váš stávající kód součástí projektu Azure Machine Learning, zkontrolujte, zda **je složka Azure Machine Learning** , abyste zajistili úspěšný převod důležitých Azure Machine Learning podrobností konfigurace, jako je například účet experimentování, pracovní prostor, který Výpočetní kontexty, které se mají použít, a další.

4. Chcete-li nastavit spouštěcí soubor, vyhledejte soubor v **Průzkumník řešení**, klikněte pravým tlačítkem myši a vyberte možnost **nastavit jako spouštěcí soubor**.

5. Spusťte program stisknutím **kombinace kláves Ctrl** +**F5** nebo výběrem možnosti **ladění > Spustit bez ladění**.

> [!div class="nextstepaction"]
> [Kurz: práce s Pythonem v aplikaci Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Viz také:

- [Ručně identifikovat existující prostředí Pythonu](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
