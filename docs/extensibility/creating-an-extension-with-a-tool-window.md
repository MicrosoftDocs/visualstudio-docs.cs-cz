---
title: Vytvoření rozšíření pomocí okna nástroje | Microsoft Docs
description: Naučte se používat šablonu projektu VSIX a šablonu položky okna vlastních nástrojů k vytvoření rozšíření s oknem nástrojů.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f956aa520bca79a84fe203093c225cfeb8389ba1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089196"
---
# <a name="create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření s oknem nástrojů

V tomto postupu se naučíte používat šablonu projektu VSIX a šablonu položky **okna vlastních nástrojů** k vytvoření rozšíření s oknem nástrojů.

## <a name="prerequisites"></a>Požadavky

 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Vytvořit okno nástroje

1. Vytvořte projekt VSIX s názvem **FirstWindow**. Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** hledáním "VSIX".

2. Po otevření projektu přidejte šablonu položky okna nástroje s názvem **MyWindow**. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V dialogovém okně **Přidat novou položku** , přejít na rozšiřitelnost v **jazyce Visual C#**  >   a vybrat **vlastní panel nástrojů**. V poli **název** v dolní části okna změňte název souboru okna nástroje na *MyWindow. cs*.

3. Sestavte projekt a spusťte ladění.

   Zobrazí se experimentální instance aplikace Visual Studio. Další informace o experimentální instanci naleznete v [experimentální instanci](../extensibility/the-experimental-instance.md).

4. V experimentální instanci přejdete do části **Zobrazit**  >  **ostatní okna**.

   Měla by se zobrazit položka nabídky pro **MyWindow**. Klikněte na něj.

   Měl by se zobrazit okno nástrojů s názvem **MyWindow** a tlačítkem **na mě.**
