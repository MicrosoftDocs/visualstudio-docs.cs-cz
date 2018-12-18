---
title: Rozšíření a přizpůsobení nástrojů Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7aac774f64d79d2d28cc690550abb7a84b7d3674
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778745"
---
# <a name="extending-and-customizing-tool-windows"></a>Rozšíření a přizpůsobení panelů nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio poskytuje několik různých typů systému windows, například okna nástrojů, okna dokumentu a dialogové okno windows. Druhy oken nástrojů jsou ostatní okna, například v okně Vlastnosti, v okně Výstup a okno seznam úkolů.  
  
## <a name="tool-windows"></a>Nástroj Windows  
 Okna nástrojů Visual Studio jsou obvykle jen pro čtení systému windows, které nejsou založené na souborech. To se liší od okna dokumentu, které zobrazí soubory v režimu čtení i zápis. **Nástrojů**, **Průzkumníka řešení**, **vlastnosti** okně a **webový prohlížeč** jsou příklady oken nástrojů.  
  
 Zjistěte, jak vytvořit okno jednoduchý nástroj, najdete v článku [přidání panelu nástrojů](../extensibility/adding-a-tool-window.md).  
  
 Registrace panelu nástrojů pomocí sady Visual Studio, naleznete v tématu [registrace panelu nástrojů](../extensibility/registering-a-tool-window.md).  
  
 Okna nástrojů jsou jednou instancí ve výchozím nastavení, což znamená, že pouze jedna instance panelu nástrojů je možné otevřít v čase. Po otevření okna nástroje jednou instancí, zůstane otevřený, dokud není zavřena integrovaného vývojového prostředí. Při zavření okna nástroje jednou instancí se změní pouze jejich viditelnost. Můžete také vytvořit více instancí okna nástrojů tak, aby více instancí okno může být otevřeno současně. Zobrazit [vytvoření panelu nástrojů s více instancemi](../extensibility/creating-a-multi-instance-tool-window.md) Další informace.  
  
 Nástroje systému windows může být *dynamické*, což znamená, že jsou viditelné pokaždé, když se použije jejich související kontextu uživatelského rozhraní. Použití automatického viditelnost můžete přehlednost oken v integrovaném vývojovém prostředí. Další informace najdete v tématu [otevření dynamického panelu nástrojů](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Nástroje systému windows může být ukotvených, s plovoucí desetinnou čárkou nebo v rámci dokument s kartami. Rámec okna nástrojů poskytuje rozhraní IDE a slouží k řízení velikosti, umístění, dokovací stavu a další trvalé vlastnosti. V podokně okna nástroje se zobrazí obsah. Výchozí velikost a umístění použít, pouze pokud panel nástrojů nejprve otevřen; potom se ukládají stav okna nástrojů.  
  
 Nástroj podokna můžete hostovat uživatelské ovládací prvky WPF a podporovat panely nástrojů. Je možné přepsat <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> vlastnost vrátí popisovač hostovaného ovládacího prvku.  
  
 Do okna nástrojů můžete přidat řadu různých funkcí. Například můžete přidat panel nástrojů: [přidání panelu nástrojů do panelu nástrojů](../extensibility/adding-a-toolbar-to-a-tool-window.md) nebo z místní nabídky: [Přidání místní nabídky v okně nástroje](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Můžete přidat ovládací prvek pro hledání, který umožňuje vyhledávat položky uvnitř okna nástroje: [přidání vyhledávání do panelu nástrojů](../extensibility/adding-search-to-a-tool-window.md).  
  
 Můžete odebírat události okna nástroje: [přihlášení k odběru události](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Rozšíření existující nástroje Windows  
 Můžete přidat informace o okno nástroje na novou **možnosti** stránky a nové nastavení na **vlastnosti** stránky, zapisovat **seznamu úkolů** a **výstup**  systému windows. Další informace najdete v tématu [rozšíření vlastností, seznamu úloh, výstup a možnosti Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) a [rozšíření vlastností, seznamu úloh, výstup a možnosti Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Modálních dialogových oken  
 V rozšíření sady Visual Studio by měl vytváření modálních dialogových oken odvozením z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, což vám umožňuje řídit jejich a zbývající části uživatelského rozhraní. Další informace najdete v tématu. [Vytváření a správa modálních dialogových oken](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md)

