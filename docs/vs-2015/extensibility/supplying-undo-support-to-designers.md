---
title: Poskytnutí podpory pro vrácení zpět pro návrháře | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675342"
---
# <a name="supplying-undo-support-to-designers"></a>Nastavení podpory fáze vrácení zpět v návrháři
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrháři, jako jsou editory, obvykle potřebují podporovat operace vrácení zpět, aby uživatelé mohli vrátit poslední změny při změně elementu kódu.  
  
 Většina návrhářů implementovaných v aplikaci Visual Studio má k dispozici podporu pro vrácení zpět automaticky poskytovanou prostředím.  
  
 Implementace návrháře, které musí poskytovat podporu pro funkci vrácení zpět:  
  
- Poskytnutí správy zpět pomocí implementace abstraktní základní třídy <xref:System.ComponentModel.Design.UndoEngine>  
  
- Zadávejte trvalost a podporu CodeDOM pomocí implementace <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> tříd a <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
  Další informace o psaní návrháře pomocí nástroje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] najdete v tématu [rozšíření podpory při návrhu](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Poskytuje výchozí infrastrukturu pro vrácení zpět podle:  
  
- Poskytování implementací pro vrácení zpět <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> prostřednictvím <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> tříd a.  
  
- Dodávání Persistence a podpora CodeDOM prostřednictvím výchozích <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> a <xref:System.ComponentModel.Design.IComponentChangeService> implementací.  
  
## <a name="obtaining-undo-support-automatically"></a>Automatické získání podpory pro vrácení zpět  
 Libovolný Návrhář vytvořený v aplikaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] má podporu automatického a úplného vrácení zpět, pokud Návrhář:  
  
- Využívá <xref:System.Windows.Forms.Control> třídu založenou na svém uživatelském rozhraní.  
  
- Využívá standardní generování a analýzu kódu založené na CodeDOM pro generování kódu a trvalost.  
  
     Další informace o práci s podporou CodeDOM sady Visual Studio naleznete v tématu [dynamické generování a kompilace zdrojového kódu](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb) .  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Kdy použít explicitní podporu pro vrácení návrháře  
 Aby návrháři používali grafické uživatelské rozhraní, které je označováno jako adaptér zobrazení, jiné než ten, který poskytuje, musí vytvořit vlastní správu zpět <xref:System.Windows.Forms.Control> .  
  
 Příkladem může být vytvoření produktu s webovým grafickým návrhovým rozhraním, nikoli pomocí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] grafického rozhraní založeného na systému.  
  
 V takových případech by bylo potřeba zaregistrovat tento adaptér zobrazení pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> a poskytnout explicitní správu zpět.  
  
 Aby návrháři nepoužívali [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model generování kódu, který je k dispozici v oboru názvů, je nutné poskytnout podporu CodeDOM a trvalosti <xref:System.CodeDom> .  
  
## <a name="undo-support-features-of-the-designer"></a>Vrátit funkce podpory v Návrháři  
 Sada SDK prostředí poskytuje výchozí implementaci rozhraní, která jsou nutná k zajištění podpory pro vrácení zpět, kterou mohou používat návrháři, kteří nepoužívají <xref:System.Windows.Forms.Control> třídy založené na jejich uživatelských rozhraních nebo standardní model CodeDOM a trvalost.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Třída je odvozena z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> třídy pomocí implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> třídy pro správu operací vrácení zpět.  
  
 Visual Studio poskytuje následující funkci pro vrácení návrháře zpět:  
  
- Propojené funkce zrušení napříč několika návrháři.  
  
- Podřízené jednotky v Návrháři mohou komunikovat s jejich rodičem implementací <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> on <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  Sada SDK prostředí poskytuje podporu CodeDOM a trvalosti tím, že poskytuje:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> jako implementace <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  A <xref:System.ComponentModel.Design.IComponentChangeService> poskytnutý [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hostitelem pro návrh.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Použití funkcí sady SDK pro prostředí k poskytnutí podpory pro vrácení zpět  
 Chcete-li získat podporu pro vrácení zpět, objekt implementující návrháře musí:  
  
- Vytvořte instanci a inicializujte instanci <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> třídy s platnou <xref:System.IServiceProvider> implementací.  
  
- Tato <xref:System.IServiceProvider> Třída musí poskytovat následující služby:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Návrháři používající [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] serializace CodeDom se mohou rozhodnout použít <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] jako implementaci rozhraní <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       V tomto případě <xref:System.IServiceProvider> by třída poskytnutá <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> konstruktoru měla vracet tento objekt jako implementaci <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> třídy.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Návrháři, kteří používají výchozí hodnoty <xref:System.ComponentModel.Design.DesignSurface> poskytované [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hostitelem pro návrh, mají zaručenou výchozí implementaci <xref:System.ComponentModel.Design.IComponentChangeService> třídy.  
  
  Návrháři implementující <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mechanismus vrácení zpět automaticky sledují změny, pokud:  
  
- Změny vlastností se provádí prostřednictvím <xref:System.ComponentModel.TypeDescriptor> objektu.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> události jsou generovány ručně, pokud je potvrzena zpětná změna.  
  
- Změny v Návrháři byly vytvořeny v kontextu <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- Návrhář rozhodne explicitně vytvořit jednotky akcí zpět pomocí standardní jednotky pro vrácení zpět, která je poskytována implementací <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> nebo implementací specifickou pro sadu Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , která je odvozena z <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> a také poskytuje implementaci obou <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Rozšíření podpory během návrhu](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
