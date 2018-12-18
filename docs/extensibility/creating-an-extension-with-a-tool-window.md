---
title: Vytváření rozšíření pomocí panelu nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6170c5d418f1778af242bb4eb08cccffe0c031be
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499800"
---
# <a name="create-an-extension-with-a-tool-window"></a>Vytváření rozšíření pomocí panelu nástrojů
V tomto postupu se dozvíte, jak použít šablonu projektu VSIX a **vlastního panelu nástrojů** šablony položky k vytvoření rozšíření pomocí panelu nástrojů.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-tool-window"></a>Vytvoření panelu nástrojů  
  
1.  Vytvořte projekt VSIX s názvem **FirstWindow**. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C#** > **rozšiřitelnost**.  
  
2.  Po otevření projektu přidat šablonu položky okna nástroje s názvem **MyWindow**. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka**. V **přidat novou položku** dialogové okno, přejděte na **Visual C#** > **rozšiřitelnost** a vyberte **vlastního panelu nástrojů**. V **název** pole v dolní části okna, změňte název souboru okna nástroje, aby *MyWindow.cs*.  
  
3.  Sestavte projekt a spusťte ladění.  
  
     Experimentální instanci sady Visual Studio se zobrazí. Další informace o experimentální instanci najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
4.  V experimentální instanci aplikace, přejděte na **zobrazení** > **ostatní Windows**.  
  
     Měli byste vidět položku nabídky pro **MyWindow**. Klikněte na něj.  
  
     Měli byste vidět okno nástroje s názvem **MyWindow** a slavným výrokem tlačítko **klikněte na mě!.**