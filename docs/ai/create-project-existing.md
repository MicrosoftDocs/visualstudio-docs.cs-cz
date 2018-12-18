---
ms.technology: vs-ai-tools
ms.openlocfilehash: 7e09023659b1f44af1951e157878d78b641be3f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915942"
---
# <a name="create-an-ai-project-from-existing-code"></a>Vytvoření projektu aplikace AI z existujícího kódu

Jakmile [nainstalované Visual Studio Tools pro AI](installation.md), snadno převést existující kód Python do projektu sady Visual Studio.

> [!Important]
> Proces je zde popsáno, ne přesuňte nebo zkopírujte původním zdrojovým souborům. Pokud chcete pracovat s kopií, duplicitní první složku.

1. Spusťte sadu Visual Studio a vyberte **soubor > Nový > projekt**.

2. V **nový projekt** dialogové okno, vyhledejte "**nástroje AI**", vyberte "**z existujícího kódu Pythonu**" šablony, dejte projektu název a umístění a vyberte **OK**.

   ![Nový projekt z existujícího kódu, krok 1](media/create-project-existing/new-ai-project.png)

3. V průvodci, který se zobrazí nastavení cesty k váš stávající kód, nastavte filtr pro typy souborů a zadejte všechny cesty pro hledání, které vyžaduje váš projekt a pak vyberte **OK**. Pokud si nejste jisti, jaké vyhledávací cesty, ponechte toto pole prázdné.

   ![Nový projekt z existujícího kódu, krok 2](media/create-project-existing/azurebatch-newproject.png)

   Pokud váš stávající kód je součástí projektu aplikace Azure Machine Learning, zkontrolujte, **složky je Azure Machine Learning** zajistit úspěšný převod důležité podrobnosti konfigurace Azure Machine Learning jako služby experimentování ve službě účet pracovního prostoru, který použití kontexty služby compute, a další.

4. Pokud chcete nastavit spouštěcí soubor, vyhledejte soubor v **Průzkumníka řešení**, klikněte pravým tlačítkem a vyberte **nastavit jako spouštěcí soubor**.

5. Spusťte program stisknutím kombinace kláves **Ctrl**+**F5** nebo jeho výběru **ladit > Spustit bez ladění**.

> [!div class="nextstepaction"]
> [Kurz: Práce s využitím Pythonu v sadě Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Viz také:

- [Ručně identifikovat existující prostředí Pythonu](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)