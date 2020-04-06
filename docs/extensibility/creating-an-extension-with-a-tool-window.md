---
title: Vytvoření rozšíření s oknem nástroje | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739538"
---
# <a name="create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření s oknem nástroje

V tomto postupu se dozvíte, jak použít šablonu projektu VSIX a šablonu **položky vlastní okno nástroje** k vytvoření rozšíření s oknem nástroje.

## <a name="prerequisites"></a>Požadavky

 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Vytvoření okna nástroje

1. Vytvořte projekt VSIX s názvem **FirstWindow**. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Při otevření projektu přidejte šablonu položky okna nástroje s názvem **MyWindow**. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** přejděte na položku**Rozšiřitelnost** **jazyka Visual C#** > a vyberte **vlastní okno nástroje**. V poli **Název** v dolní části okna změňte název souboru okna nástroje na *MyWindow.cs*.

3. Sestavení projektu a začít ladění.

   Zobrazí se experimentální instance sady Visual Studio. Další informace o experimentální instanci naleznete [v tématu Experimentální instance](../extensibility/the-experimental-instance.md).

4. V experimentální instanci přejděte na **zobrazit** > **jiné windows**.

   Měla by se zobrazit položka nabídky pro **MyWindow**. Klikněte na něj.

   Měli byste vidět okno nástroje s názvem **MyWindow** a tlačítko s nápisem **Click Me!.**
