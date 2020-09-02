---
title: Správa sady nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 5eeb5d06b0e689391f450fec8744fa58a41f4508
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681544"
---
# <a name="managing-the-toolbox"></a>Správa sady nástrojů
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Umožňuje VSPackage, jako je editor nebo Návrhář, spravovat členství a vzhled sady **nástrojů**.  
  
 Kromě toho je možné spravovat samotný **panel nástrojů** pomocí automatizace. Další informace o správě sady nástrojů prostřednictvím automatizace naleznete v tématu [How to: Control a Toolbox](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Automatický výběr karty panelu nástrojů  
 Konkrétní kartu nebo kategorii **panelu nástrojů** lze automaticky aktivovat v závislosti na tom, který editor nebo Návrhář je aktuálně aktivní. Například pokud je Návrhář formulářů aktivovaný, můžete chtít, aby byla vybraná karta **všechny model Windows Forms** .  
  
 Tato podpora je omezená na editory a návrháře, které vyžadují:  
  
1. Implementace objektu factory pro poskytování instancí editoru nebo návrháře. Další informace o implementaci objektu Object Factory návrháře nebo editoru najdete v tématu věnovaném objektům pro vytváření [editorů](../extensibility/editor-factories.md).  
  
2. Registrace karty panelu nástrojů, která se automaticky aktivuje, pokud je přítomen Editor nebo Návrhář.  
  
## <a name="controlling-the-toolbox"></a>Řízení sady nástrojů  
 Doplňková podpora automatizace [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] poskytuje následující rozhraní pro zajištění větší kontroly nad tím, jak je **Sada nástrojů** spravovaná.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Umožňuje aplikacím spravovat, přidávat a odebírat <xref:System.Drawing.Design.ToolboxItem> objekty ze **sady nástrojů**. Umožňuje také konfiguraci kategorií vzhledů a **nástrojů** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Umožňuje aplikacím spravovat, přidávat a odebírat ovládací prvky **sady nástrojů** založené na aktivním prostředí a také konfigurovat kategorie a vzhled **panelu nástrojů** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Rozšiřuje funkčnost, která se nachází v nástroji <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> , a zajišťuje tak úplnou podporu pro trvalost a lokalizaci.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Při práci s těmito rozhraními je potřeba vzít v úvahu několik důležitých bodů:  
  
- <xref:System.Drawing.Design.IToolboxService> je k dispozici pouze pro sady VSPackage spravované pomocí architektury Package.  
  
- Ovládací prvky nelze přidat přímo do **sady nástrojů** pomocí <xref:System.Drawing.Design.IToolboxService> .  
  
- VSPackage musí buď použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> pro přidání ovládacích prvků nebo hostování ovládacího prvku v ovládacím prvku obálky, který je odvozen z <xref:System.Windows.Forms.AxHost> .  
  
   Visual Studio poskytuje `Aximp.exe` Nástroj pro automatizaci zalamování ovládacího prvku ActiveX v ovládacím prvku odvozeném z <xref:System.Windows.Forms.AxHost> . Další informace najdete v tématu [Aximp.exe (model Windows Forms Importéru ovládacího prvku ActiveX)](https://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> jsou rozhraní založená na modelu COM dostupná prostřednictvím sestavení vzájemné spolupráce.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> je odvozen z <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> a implementuje všechny metody.  
  
   Objekty získávají pouze instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> není odvozen z <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> a neimplementuje své metody.  
  
   Objekty, které potřebují funkce v obou rozhraních, musí z prostředí získávat instance obou rozhraní.  
  
- Při práci s <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> a jsou <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> informace o kanonickém (nelokalizovaných) názvech karet zpracovávány <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> metodami a.  
  
- Při použití <xref:System.Drawing.Design.IToolboxService> je až do implementátora spravovat lokalizované informace, jako jsou názvy kategorií.  
  
  Pomocí mechanismu nastavení můžete uživatelům povolit ukládání nastavení **sady nástrojů** , ke kterým uživatelé přistupovali z příkazu **Import/Export nastavení** , který najdete v nabídce **nástroje** IDE. Další informace o tom, jak používat nastavení, najdete v tématu [rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření panelu nástrojů](../misc/extending-the-toolbox.md)