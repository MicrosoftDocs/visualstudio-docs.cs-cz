---
ms.topic: include
ms.openlocfilehash: 47c390fbc7a6f84c25d4bde0317985bd149cae2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89324783"
---
1. Spusťte Visual Studio a vyberte **soubor**  >  **Nový**  >  **projekt**.

1. V dialogovém okně **Nový projekt** vyhledejte "Python", vyberte **z existující šablony kódu Python** , zadejte název a umístění projektu a vyberte **OK**.

1. V průvodci, který se zobrazí, nastavte cestu k vašemu existujícímu kódu, nastavte filtr pro typy souborů a zadejte všechny cesty pro hledání, které váš projekt vyžaduje, a pak vyberte **Další**. Pokud si nejste jisti, jaké vyhledávací cesty jsou, ponechte toto pole prázdné.

    ![Nový projekt z existujícího kódu, krok 1](../media/projects-from-existing-1.png)

1. V dalším dialogovém okně vyberte spouštěcí soubor pro váš projekt a vyberte **Další**. (V případě potřeby vyberte prostředí; v opačném případě přijměte výchozí hodnoty.) Všimněte si, že se v dialogovém okně zobrazují pouze soubory v kořenové složce. Pokud se požadovaný soubor nachází v podsložce, ponechte spouštěcí soubor prázdný a nastavte ho později v **Průzkumník řešení** (popsané níže).

    ![Nový projekt z existujícího kódu, krok 2](../media/projects-from-existing-2.png)

1. Vyberte umístění, do kterého se má soubor projektu Uložit (což je soubor *. pyproj* na disku). V případě potřeby můžete také zahrnout automatické rozpoznávání virtuálních prostředí a přizpůsobit projekt pro různá webová rozhraní. Pokud si nejste jisti těmito možnostmi, nechte je nastavené na výchozí hodnoty.

    ![Nový projekt z existujícího kódu, krok 3](../media/projects-from-existing-3.png)

1. Vyberte **Dokončit** a Visual Studio vytvoří projekt a otevře ho v **Průzkumník řešení**. Pokud chcete soubor *. pyproj* přesunout jinam, vyberte ho v **Průzkumník řešení** a zvolte **soubor**  >  **Uložit jako**. Tato akce aktualizuje odkazy na soubory v projektu, ale nepřesouvá žádné soubory kódu.

1. Chcete-li nastavit jiný spouštěcí soubor, vyhledejte soubor v **Průzkumník řešení**, klikněte pravým tlačítkem myši a vyberte možnost **nastavit jako spouštěcí soubor**.