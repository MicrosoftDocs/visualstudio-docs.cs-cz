---
ms.topic: include
ms.openlocfilehash: 47c390fbc7a6f84c25d4bde0317985bd149cae2f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "68159591"
---
1. Spusťte Visual Studio a vyberte **Soubor** > **nový** > **projekt**.

1. V dialogovém okně **Nový projekt** vyhledejte "Python", vyberte **šablonu kódu Z existujícího pythonu,** pojmenujte projekt a vyberte **OK**.

1. V průvodci, který se zobrazí, nastavte cestu k existujícímu kódu, nastavte filtr pro typy souborů a určete všechny cesty hledání, které projekt vyžaduje, a pak vyberte **Další**. Pokud nevíte, jaké jsou vyhledávací cesty, ponechte toto pole prázdné.

    ![Nový projekt z existujícího kódu, krok 1](../media/projects-from-existing-1.png)

1. V dalším dialogovém okně vyberte spouštěcí soubor projektu a vyberte **Další**. (V případě potřeby vyberte prostředí; jinak přijměte výchozí hodnoty.) Všimněte si, že dialogové okno zobrazuje pouze soubory v kořenové složce; Pokud je požadovaný soubor v podsložce, ponechejte spouštěcí soubor prázdný a nastavte jej později v **Průzkumníku řešení** (popsaném níže).

    ![Nový projekt z existujícího kódu, krok 2](../media/projects-from-existing-2.png)

1. Vyberte umístění, do kterého chcete soubor projektu uložit (což je soubor *Pyproj* na disku). Pokud je to možné, můžete také zahrnout automatické zjišťování virtuálních prostředí a přizpůsobit projekt pro různé webové architektury. Pokud si nejste jisti těmito možnostmi, ponechte je nastavené na výchozí hodnoty.

    ![Nový projekt z existujícího kódu, krok 3](../media/projects-from-existing-3.png)

1. Vyberte **Dokončit** a Visual Studio vytvoří projekt a otevře jej v **Průzkumníku řešení**. Pokud chcete soubor *Pyproj* přesunout jinam, vyberte ho v **Průzkumníku řešení** a zvolte **Uložit soubor** > **jako**. Tato akce aktualizuje odkazy na soubory v projektu, ale nepřesune žádné soubory kódu.

1. Chcete-li nastavit jiný spouštěcí soubor, vyhledejte jej v **Průzkumníku řešení**, klepněte pravým tlačítkem myši a vyberte **příkaz Nastavit jako spouštěcí soubor**.