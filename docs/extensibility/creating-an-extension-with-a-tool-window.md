---
title: Vytvoření rozšíření pomocí okna nástroje | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 597b84854dd398abee9dc21090e085273bc94c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903897"
---
# <a name="create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření s oknem nástrojů

V tomto postupu se naučíte používat šablonu projektu VSIX a šablonu položky **okna vlastních nástrojů** k vytvoření rozšíření s oknem nástrojů.

## <a name="prerequisites"></a>Předpoklady

 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Vytvořit okno nástroje

1. Vytvořte projekt VSIX s názvem **FirstWindow**. Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** hledáním "VSIX".

2. Po otevření projektu přidejte šablonu položky okna nástroje s názvem **MyWindow**. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V dialogovém okně **Přidat novou položku** , přejít na rozšiřitelnost v **jazyce Visual C#**  >  **Extensibility** a vybrat **vlastní panel nástrojů**. V poli **název** v dolní části okna změňte název souboru okna nástroje na *MyWindow.cs*.

3. Sestavte projekt a spusťte ladění.

   Zobrazí se experimentální instance aplikace Visual Studio. Další informace o experimentální instanci naleznete v [experimentální instanci](../extensibility/the-experimental-instance.md).

4. V experimentální instanci přejdete do části **Zobrazit**  >  **ostatní okna**.

   Měla by se zobrazit položka nabídky pro **MyWindow**. Klikněte na něj.

   Měl by se zobrazit okno nástrojů s názvem **MyWindow** a tlačítkem **na mě.**
