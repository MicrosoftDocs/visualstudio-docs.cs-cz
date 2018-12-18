---
title: Správa sady nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: douge
ms.openlocfilehash: 227001e827057ffab4c851a985f7e36afaf0f351
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873419"
---
# <a name="managing-the-toolbox"></a>Správa sady nástrojů
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Umožňuje VSPackage, například návrháři nebo editoru pro správu členství a vzhled **nástrojů**.  
  
 Kromě toho **nástrojů** samotný můžete spravovat pomocí služby automation. Další informace o správě nástrojů díky automatizaci, naleznete v tématu [postupy: řízení panelu nástrojů](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Výběr karty automatické sady nástrojů  
 Konkrétní **nástrojů** kartu nebo kategorie automaticky provádět aktivní na základě toho, jaké editoru nebo návrháře aktuálně aktivní. Například pokud je aktivovaná Návrháře formulářů, můžete **všechny formuláře Windows** vybraná karta.  
  
 Tato podpora je omezena na editorů a návrhářů, které vyžadují:  
  
1.  Implementace objektu factory pro instance editoru nebo návrháře. Další informace o implementaci objektu factory návrháři nebo editoru, najdete v části [objekty pro vytváření editoru](../extensibility/editor-factories.md).  
  
2.  Registrace na kartu panelu nástrojů, která automaticky se aktivuje v případě, že je k dispozici editoru nebo návrháře.  
  
## <a name="controlling-the-toolbox"></a>Řízení panelu nástrojů  
 Doplnění podpory služby automation [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] poskytuje následující rozhraní k poskytování rozšíření VSPackages větší kontrolu nad jak **nástrojů** spravuje.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Umožňuje aplikacím, které chcete spravovat, přidávat a odebírat <xref:System.Drawing.Design.ToolboxItem> objekty z **nástrojů**. Také umožňuje konfiguraci toho, vzhled a **nástrojů** kategorií.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Umožňuje spravovat, přidávat a odebírat aplikace založené na aktivní **nástrojů** ovládací prvky, stejně jako konfiguraci **nástrojů** kategorie a vzhled.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Rozšiřuje funkce součástí <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> tím, že poskytuje úplnou podporu pro trvalost a lokalizaci.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Existuje několik důležitých bodů potřeba mít na paměti při práci s těmito rozhraními:  
  
- <xref:System.Drawing.Design.IToolboxService> je k dispozici pouze na základě Managed Package Framework VSPackages.  
  
- Ovládací prvky nelze přímo přidat do **nástrojů** pomocí <xref:System.Drawing.Design.IToolboxService>.  
  
- VSPackage musí buď použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> můžete přidat ovládací prvky nebo hostování ovládacího prvku v ovládacím prvku obálky, která je odvozena z <xref:System.Windows.Forms.AxHost>.  
  
   Visual Studio poskytuje `Aximp.exe` nástroj pro automatizaci zabalení ovládacího prvku ActiveX v ovládacím prvku odvozený od <xref:System.Windows.Forms.AxHost>. Další informace najdete v tématu [Aximp.exe (Importér ovládacích prvků ActiveX formulářů Windows)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> jsou k dispozici prostřednictvím sestavení vzájemné spolupráce COM rozhraní.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> je odvozen od <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> a implementuje všechny metody.  
  
   Objekty získat jenom instanci <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> není odvozen od <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> a neimplementuje její metody.  
  
   Objekty funkce v obou rozhraní by bylo nutné získat instance obou rozhraní z prostředí.  
  
- Při práci s <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, informace o kanonické (Nelokalizováno) názvy karet zařizuje služba <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> metody.  
  
- Při použití <xref:System.Drawing.Design.IToolboxService>, je až implementátora ke správě lokalizované informace, jako jsou názvy kategorií.  
  
  Použít mechanismus nastavení umožňují uživatelům ukládat **nástrojů** nastavení přístup uživatelé ze **Importovat/exportovat nastavení** příkaz v rozhraní IDE **nástroje** nabídky. Další informace o tom, jak používat nastavení najdete v tématu [rozšíření uživatelská nastavení a možnosti](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření sady nástrojů](../misc/extending-the-toolbox.md)