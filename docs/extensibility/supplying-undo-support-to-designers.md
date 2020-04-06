---
title: Poskytování podpory odčinit návrháře | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699677"
---
# <a name="supply-undo-support-to-designers"></a>Dodávat podporu pro odvádělte návrhářům

Návrháři, jako jsou editory, obvykle potřebují podporovat operace zpět, aby uživatelé mohli stornovat své poslední změny při úpravách prvku kódu.

Většina návrhářů implementovaných v sadě Visual Studio má podporu "vrátit" automaticky poskytovanou prostředím.

Návrhářské implementace, které potřebují poskytnout podporu pro funkci vrátit:

- Zadejte správu vrátit se k nápravě implementací abstraktní základní třídy<xref:System.ComponentModel.Design.UndoEngine>

- Zabezpečení napájení a CodeDOM podporu <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> implementací a <xref:System.ComponentModel.Design.IComponentChangeService> třídy.

Další informace o psaní návrhářů pomocí rozhraní .NET Framework naleznete [v tématu Rozšíření podpory návrhu .](/previous-versions/37899azc(v=vs.140))

Poskytuje [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] výchozí infrastrukturu vrátit do aplikace:

- Poskytování implementace správy vrátit <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> vrátit <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> prostřednictvím a třídy.

- Poskytování perzistence a codedom podporu prostřednictvím výchozí <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> a <xref:System.ComponentModel.Design.IComponentChangeService> implementace.

## <a name="obtain-undo-support-automatically"></a>Získat podporu vrátit do aplikace automaticky

Každý návrhář vytvořený v sadě Visual Studio má automatickou a úplnou podporu vrátit, pokud návrhář:

- Využívá třídu <xref:System.Windows.Forms.Control> založenou pro své uživatelské rozhraní.

- Používá standardní codedom na generování kódu a analýzy systému pro generování kódu a trvalost.

   Další informace o práci s podporou Visual Studio CodeDOM naleznete [v tématu Dynamické generování zdrojového kódu a kompilace](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Kdy použít podporu explicitního návrháře vrátit se k podpoře
 Návrháři musí zadat vlastní správu vrátit se k nápravě, pokud používají grafické uživatelské <xref:System.Windows.Forms.Control>rozhraní, označované jako adaptér zobrazení, jiné než dodané společností .

 Příkladem může být vytvoření produktu s webovým grafickým návrhovým rozhraním, nikoli s grafickým rozhraním založeným na rozhraní .NET Framework.

 V takových případech by bylo nutné zaregistrovat tento <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>adaptér zobrazení pomocí sady Visual Studio a poskytnout explicitní správu vrátit vrátit.

 Návrháři musí poskytnout CodeDOM a trvalost podporu, pokud nepoužívají model <xref:System.CodeDom> generování kódu sady Visual Studio k dispozici v oboru názvů.

## <a name="undo-support-features-of-the-designer"></a>Vrátit funkce podpory návrháře
 Sada Environment SDK poskytuje výchozí implementace rozhraní potřebných k poskytování podpory vrátit <xref:System.Windows.Forms.Control> do aplikace, kterou mohou použít návrháři, kteří nepoužívají třídy založené pro jejich uživatelská rozhraní nebo standardní model CodeDOM a perzistence.

 Třída <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> je odvozena od <xref:System.ComponentModel.Design.UndoEngine> třídy .NET <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> Framework pomocí implementace třídy ke správě operací vrátit se k aplikaci.

 Visual Studio poskytuje následující funkce pro návrháře vrátit:

- Propojené funkce vrátit do aplikace mezi více návrháři.

- Podřízené jednotky v rámci návrháře mohou <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> komunikovat <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>se svými rodiči implementací a zapnutou .

Sada Environment SDK poskytuje codedom a trvalost podporu tím, že poskytuje:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>jako provádění<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Poskytované <xref:System.ComponentModel.Design.IComponentChangeService> hostitele mno že návrže sady Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Použití funkcí sady Environment SDK k poskytování podpory zrušení

Chcete-li získat podporu vrátit, objekt implementující návrháře musí vytvořit instanci a inicializovat instanci <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> třídy s platnou <xref:System.IServiceProvider> implementací. Tato <xref:System.IServiceProvider> třída musí poskytovat následující služby:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Návrháři pomocí serializace Visual Studio CodeDOM může zvolit použití <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> dodaný [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] s jako jeho implementace <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   V tomto případě <xref:System.IServiceProvider> třídy poskytované <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> konstruktoru by měl vrátit <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> tento objekt jako implementace třídy.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Návrháři pomocí <xref:System.ComponentModel.Design.DesignSurface> výchozí poskytované hostitele návrhu sady Visual Studio je <xref:System.ComponentModel.Design.IComponentChangeService> zaručeno, že výchozí implementaci třídy.

Návrháři implementující mechanismus zpět <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> na základě automaticky sleduje změny, pokud:

- Změny vlastností jsou <xref:System.ComponentModel.TypeDescriptor> prováděny prostřednictvím objektu.

- <xref:System.ComponentModel.Design.IComponentChangeService>události jsou generovány ručně při zrušení změny je potvrzena.

- Modifikace na projektantu byla <xref:System.ComponentModel.Design.DesignerTransaction>vytvořena v kontextu .

- Návrhář se rozhodne explicitně vytvořit jednotky vrátit pomocí standardní jednotky vrátit <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> do aplikace poskytované implementací aplikace <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>nebo specifické pro implementaci sady Visual Studio , která je odvozena <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> z a také poskytuje implementaci obou <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Rozšířit podporu návrhu](/previous-versions/37899azc(v=vs.140))
