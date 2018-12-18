---
title: Poskytnutí zpět podporu, aby návrháři | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ba86f77219329c0e34edecf10aca69e8bedf2226
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843233"
---
# <a name="supplying-undo-support-to-designers"></a>Nastavení podpory fáze vrácení zpět v návrháři
Návrháře, jako jsou editory, obvykle musí podporovat operace vrácení zpět tak, aby uživatelé lze zrušit jejich poslední změny při úpravě prvek kódu.  
  
 Většina návrháři implementované v sadě Visual Studio podporují zpět automaticky poskytovaných prostředím.  
  
 Návrháře implementace, které potřebují k poskytování podpory pro funkci vrácení zpět:  
  
- Poskytování správy zpět díky implementaci abstraktní základní třída <xref:System.ComponentModel.Design.UndoEngine>  
  
- Podpora dodávky trvalosti a CodeDOM implementací <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> a <xref:System.ComponentModel.Design.IComponentChangeService> třídy.  
  
  Další informace o vytváření pomocí návrháře [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], naleznete v tématu [rozšíření podpory během návrhu](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Poskytuje infrastrukturu výchozí zpět podle:  
  
- Poskytuje správu implementace prostřednictvím zpět <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> a <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> třídy.  
  
- Poskytnutí trvalosti a podpora CodeDOM výchozí <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> a <xref:System.ComponentModel.Design.IComponentChangeService> implementace.  
  
## <a name="obtaining-undo-support-automatically"></a>Získání podpory zpět automaticky  
 Všechny návrháře vytvořené v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podporuje automatické a úplné zpět if, návrháře:  
  
-   Využívá <xref:System.Windows.Forms.Control> na základě třídy pro jeho uživatelské rozhraní.  
  
-   Využívá standardní kód založený na CodeDOM generování a systém analýzy pro generování kódu a uchovávání.  
  
     Další informace o práci s podporou Visual Studio CodeDOM naleznete v tématu [dynamické generování zdrojového kódu a kompilace](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Kdy použít podpora pro explicitní návrháře vracení zpět  
 Návrháři musíte zadat management své vlastní vrácení zpět, je-li využívají grafické uživatelské rozhraní, označuje jako zobrazení adaptér, než poskytuje <xref:System.Windows.Forms.Control>.  
  
 Příkladem může být vytváření produktu se rozhraní založeného na webu grafickou návrhovou spíše než [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] na základě grafického rozhraní.  
  
 V takových případech by jedna muset zaregistrovat tento adaptér zobrazení s [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pomocí <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>a zajistit správu explicitní vrácení zpět.  
  
 Návrháři muset zadat CodeDOM a trvalost podporují, pokud se nepoužívají [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] součástí modelu generování kódu <xref:System.CodeDom> obor názvů.  
  
## <a name="undo-support-features-of-the-designer"></a>Zrušit podporu funkce návrháře  
 Sada SDK prostředí poskytuje výchozí implementaci rozhraní potřebných k poskytování zpět podporu, která je možné pomocí Návrháře bez použití <xref:System.Windows.Forms.Control> na základě třídy pro jejich uživatelských rozhraní nebo standardní model CodeDOM a trvalost.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Třída odvozena z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> pomocí implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> třídy ke správě zrušení operací.  
  
 Visual Studio poskytuje následující funkce návrháře vrácení zpět:  
  
- Propojená operace vrácení zpět funkce napříč více návrháře.  
  
- Podřízené jednotky v rámci návrháře otevřeného svých nadřazených složek implementací <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> na <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
  Sada SDK prostředí poskytuje podporu CodeDOM a stálost zadáním:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> jako implementací služby <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  A <xref:System.ComponentModel.Design.IComponentChangeService> poskytované [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]"návrhu hostitele.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Pomocí funkce SDK prostředí slouží k poskytování podpora pro vracení zpět  
 Získání podpory vrácení zpět, musí objekt implementace návrháře:  
  
- Konkretizovat a inicializovat instanci <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> třídy s platným <xref:System.IServiceProvider> implementace.  
  
- To <xref:System.IServiceProvider> třída musí poskytovat následující služby:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
     Pomocí návrhářů [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v případě serializace CodeDOM rozhodnout pro použití <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> součástí [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] jako jeho implementace <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
     V takovém případě <xref:System.IServiceProvider> třídy, které jsou k dispozici na <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> konstruktor by měl vrátit tento objekt jako implementace <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> třídy.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
     Použití výchozí hodnoty návrháře <xref:System.ComponentModel.Design.DesignSurface> poskytované [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] návrhu hostitele je zaručeno, že má výchozí implementaci třídy <xref:System.ComponentModel.Design.IComponentChangeService> třídy.  
  
  Implementace návrhářů <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> zpět na základě mechanismu automaticky sleduje změny, pokud:  
  
- Až dojde ke změně vlastnosti <xref:System.ComponentModel.TypeDescriptor> objektu.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> události jsou generovány ručně, pokud je vrátit změny potvrzeny.  
  
- Změny v Návrháři byl vytvořen v rámci kontextu <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
- Návrhář vybere explicitně vytvořit buď pomocí jednotky akcí zpět standardní jednotku poskytuje implementaci pro <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> nebo Visual Studio specifickou implementaci <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, která je odvozena z <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> a poskytuje provádění obou <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Rozšíření podpory během návrhu](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)