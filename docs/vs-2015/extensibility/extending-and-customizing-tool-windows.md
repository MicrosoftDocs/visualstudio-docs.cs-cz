---
title: Rozšíření a přizpůsobení oken nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b232fa1275bce453e3b32cea6a5ff37fdd501c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204546"
---
# <a name="extending-and-customizing-tool-windows"></a>Rozšíření a přizpůsobení panelů nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio poskytuje několik různých typů oken, například okna nástrojů, okna dokumentů a dialogová okna. Další okna, jako je okno Vlastnosti, okno výstup a okno Seznam úkolů, jsou typy oken nástrojů.  
  
## <a name="tool-windows"></a>Okna nástrojů  
 Okna nástrojů sady Visual Studio jsou obvykle okna jen pro čtení, která nejsou založená na souborech. V takovém případě se liší od oken dokumentu, které zobrazují soubory v režimu pro čtení i zápis. Příklady oken nástrojů jsou **panely nástrojů**, **Průzkumník řešení**, okno **vlastnosti** a **webový prohlížeč** .  
  
 Chcete-li zjistit, jak vytvořit jednoduchý panel nástrojů, přečtěte si téma [Přidání okna nástroje](../extensibility/adding-a-tool-window.md).  
  
 Chcete-li zaregistrovat okno nástrojů se sadou Visual Studio, přečtěte si téma [registrace okna nástroje](../extensibility/registering-a-tool-window.md).  
  
 Okna nástrojů jsou ve výchozím nastavení jediná instance, což znamená, že v jednom okamžiku může být otevřena pouze jedna instance okna nástroje. Po otevření okna nástroje s jednou instancí zůstane otevřené, dokud se IDE nezavře. Při zavření okna nástroje s jednou instancí se změní pouze jeho viditelnost. Můžete také vytvořit okna nástrojů s více instancemi, aby bylo možné současně otevřít více instancí okna. Další informace najdete v tématu [vytvoření panelu s více instancemi](../extensibility/creating-a-multi-instance-tool-window.md) .  
  
 Okna nástrojů mohou být *Dynamická*, což znamená, že jsou viditelné vždy, když platí jejich související kontext uživatelského rozhraní. Použití automatického viditelnosti může snížit zbytečně velký počet oken v integrovaném vývojovém prostředí (IDE). Další informace naleznete v tématu [otevření dynamického okna nástroje](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Okna nástrojů lze ukotvit, plovoucí nebo se záložkami v rámci rámce dokumentu. Rámec okna nástroje je poskytován rozhraním IDE a slouží k řízení velikosti, umístění, stavu ukotvení a dalších trvalých vlastností. Obsah se zobrazí v podokně okna nástroje. Výchozí velikost a umístění platí pouze při prvním otevření okna nástroje; po tom, co je stav okna nástroje trvalé.  
  
 Podokna okna nástroje mohou hostovat uživatelské ovládací prvky WPF a podporují panely nástrojů. Můžete přepsat <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> vlastnost a vrátit tak popisovač hostovaného ovládacího prvku.  
  
 Do oken nástrojů můžete přidat mnoho různých funkcí. Například můžete přidat panel nástrojů: [Přidání panelu nástrojů do panelu](../extensibility/adding-a-toolbar-to-a-tool-window.md) nástrojů nebo místní nabídky: [Přidání místní nabídky do okna nástroje](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Můžete přidat ovládací prvek hledání, který umožňuje hledat položky v okně nástroje: [Přidání vyhledávání do okna nástroje](../extensibility/adding-search-to-a-tool-window.md).  
  
 Můžete se přihlásit k odběru událostí okna nástroje: [přihlášení k odběru události](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Rozšíření existujících oken nástrojů  
 Můžete přidat informace o okně nástroje na novou stránku **Možnosti** a nové nastavení na stránce **vlastnosti** a zapsat do oken **seznam úkolů** a **výstup** . Další informace najdete v tématu [rozšíření vlastností, seznam úkolů, výstupu a oken možností](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) a [rozšíření vlastností, seznam úkolů, výstupu a oken možností](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Modální dialogová okna  
 V rozšíření sady Visual Studio byste měli vytvořit modální dialogová okna jejich odvozením z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , což umožňuje jejich kontrolu a zbytek uživatelského rozhraní. Další informace najdete na webu . [Vytváření a Správa modálních](../extensibility/creating-and-managing-modal-dialog-boxes.md)dialogových oken.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md)
