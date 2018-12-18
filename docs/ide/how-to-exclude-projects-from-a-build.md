---
title: 'Postupy: vyloučení projektů ze sestavení'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e203fd9f1515e212591afe11c246cdeb78201b8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949981"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Postupy: vyloučení projektů ze sestavení

Můžete vytvořit řešení bez vytváření všechny projekty, které obsahuje. Například může vyloučit projekt, který dělí sestavení. Je pak sestavení projektu po byste prozkoumat a adresu problémy.

Pomocí následujících postupů můžete vyloučit projektu:

-   Odstraněním dočasně konfigurace aktivního řešení.

-   Vytvoření konfigurace řešení, která neobsahuje projekt.

Další informace najdete v tématu [Rady pro pochopení konfigurace sestavení](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Dočasně odebrání konfigurace aktivního řešení projektu

1.  Na řádku nabídek zvolte **sestavení** > **nástroje Configuration Manager**.

2.  V **projektu kontexty** tabulky, vyhledejte projektu, které chcete vyloučit z buildu.

3.  V **sestavení** sloupce projektu, zrušte zaškrtnutí políčka.

4.  Vyberte **Zavřít** tlačítko a pak znovu sestavte řešení.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Pro vytvoření konfigurace řešení, které vylučuje projektu

1.  Na řádku nabídek zvolte **sestavení** > **nástroje Configuration Manager**.

2.  V **aktivní konfigurace řešení** vyberte  **\<nový >**.

3.  V **název** pole, zadejte název pro konfiguraci řešení.

4.  V **Kopírovat nastavení z** vyberte konfigurace řešení, na kterém chcete vytvořit novou konfiguraci (například **ladění**) a potom zvolte **OK** tlačítko .

5.  V **nástroje Configuration Manager** dialogové okno, zrušte zaškrtnutí políčka v **sestavení** sloupec pro projekt, který chcete vyloučit a potom vyberte **Zavřít** tlačítko.

6.  Na **standardní** nástrojů ověřte, zda se nová konfigurace řešení je aktivní konfigurace v **konfigurace řešení** pole.

7.  Na řádku nabídek zvolte **sestavení** > **znovu sestavit řešení**.

## <a name="see-also"></a>Viz také

- [Pochopení konfigurace sestavení](../ide/understanding-build-configurations.md)
- [Postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Postupy: sestavení více konfigurací současně](../ide/how-to-build-multiple-configurations-simultaneously.md)