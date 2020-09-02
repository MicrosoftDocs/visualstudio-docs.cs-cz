---
title: Zpracování příkazů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184377"
---
# <a name="command-handling"></a>Zpracování příkazů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor může definovat nové příkazy. Příkazy jsou obvykle zobrazeny v nabídce, na panelu nástrojů nebo v místní nabídce.  
  
 Další informace o definování příkazů a nabídek naleznete v tématech [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Služba jazyka může řídit, které kontextové nabídky se zobrazí v editoru, zachycením <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> výčtu. Alternativně můžete řídit kontextovou nabídku u jednotlivých značek. Další informace najdete v tématu [Důležité příkazy pro filtry služby jazyka](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Přidání příkazů do kontextové nabídky editoru  
 Chcete-li přidat příkaz do kontextové nabídky, je nutné nejprve definovat sadu příkazů nabídky, které patří do konkrétní skupiny. Následující příklad je pořízen ze souboru. vsct vygenerovaného jako součást návodu [Návod: Přidání funkcí do vlastního editoru](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>Místní nabídka CustomEditor\</ButtonText>  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 Výše uvedený text přidá do **kontextové nabídky text CustomEditor**kontextovou nabídku. Identifikátor GUID nabídky je sada příkazů, která je vytvořena pomocí tohoto editoru, a typ je "Context".  
  
 Můžete také použít předdefinované příkazy, které nemusejí být definovány v souboru. vsct. Například pokud prohlížíte soubor EditorPane.cs vygenerovaný šablonou balíčku sady Visual Studio, zjistíte, že sada předdefinovaných příkazů, jako je <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definována pomocí <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> , je zpracována v obslužných rutinách příkazů, jako je například metoda onSelectAll.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
