---
title: 'Postupy: Vytváření vlastních grafů ve výsledcích zátěžového testu'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c65b9ad5c6a9d554f2c71cc5d17c63ce9368df2c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055397"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Postupy: vytváření vlastních grafů v načítání výsledků testu

Můžete navrhovat grafy, které zobrazí konkrétní informace o výsledcích zátěžového testu. Navrhněte vlastní graf tak, že zadáte počítadla testu zatížení, které se zobrazí grafu.

Následující postup můžete provést při spuštění zátěžového testu nebo po jeho dokončení.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>K vytvoření grafu výsledků vlastní zátěžového testu

1.  Na **zátěžový Test** nástrojů, zvolte **přidat nový graf**.

     \- nebo –

     Na **Analyzéru zátěžového testu**, klikněte pravým tlačítkem **čítače** panelu nebo v grafu a pak vyberte **přidat graf**.

     **Zadejte název grafu** se zobrazí dialogové okno.

2.  V části **název grafu**, zadejte název pro graf a zvolte **OK**.

     Nový graf se zobrazí v **Analyzéru zátěžového testu**. Zobrazí se v panelu aktuálně vybranému grafu. nahradí grafu, který se zobrazí v panelu.

3.  Nový graf přizpůsobte tak, že přidáte čítače. Další informace najdete v tématu [postupy: Přidání a odstranění čítačů pro grafy](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>Viz také:

- [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Postupy: Přidání a odstranění čítačů pro grafy](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)