---
title: Vytvoření rozšíření pomocí okna nástroje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431846"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Vytváření rozšíření pomocí panelu nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto postupu se naučíte používat šablonu projektu VSIX a šablonu položky **okna vlastních nástrojů** k vytvoření rozšíření s oknem nástrojů.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Vytvoření okna nástrojů  
  
1. Vytvořte projekt VSIX s názvem **FirstWindow**. Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** v části **Visual C#/rozšiřitelnost**.  
  
2. Po otevření projektu přidejte šablonu položky okna nástroje s názvem **FirstWindow**. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat/nová položka**. V dialogovém okně **Přidat novou položku** přejdete na **Visual C#/rozšiřitelnost** a vyberte **vlastní panel nástrojů**. V poli **název** v dolní části okna změňte název souboru okna nástroje na **FirstWindow.cs**.  
  
3. Sestavte projekt a spusťte ladění.  
  
     Zobrazí se experimentální instance aplikace Visual Studio. Další informace o experimentální instanci naleznete v [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
4. V experimentální instanci přejdete do **zobrazení/dalších oken**.  
  
     Měla by se zobrazit položka nabídky pro **FirstWindow**. Klikněte na něj.  
  
     Měl by se zobrazit okno nástrojů s názvem **FirstWindow** a tlačítkem **na mě.**
