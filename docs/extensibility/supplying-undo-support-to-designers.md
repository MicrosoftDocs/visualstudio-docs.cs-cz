---
title: Poskytnutí podpory pro vrácení zpět pro návrháře | Microsoft Docs
description: Přečtěte si, jak poskytnout podporu pro vrácení zpět v návrhářích, a to buď automaticky, nebo pomocí funkcí v sadě Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b56eb762cf4a2746af04ed69c7c4c49afc15dec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056308"
---
# <a name="supply-undo-support-to-designers"></a>Poskytnutí podpory pro vrácení zpět návrhářům

Návrháři, jako jsou editory, obvykle potřebují podporovat operace vrácení zpět, aby uživatelé mohli vrátit poslední změny při změně elementu kódu.

Většina návrhářů implementovaných v aplikaci Visual Studio má podporu "zpět", která je automaticky poskytována prostředím.

Implementace návrháře, které musí poskytovat podporu pro funkci vrácení zpět:

- Poskytnutí správy zpět pomocí implementace abstraktní základní třídy <xref:System.ComponentModel.Design.UndoEngine>

- Zadávejte trvalost a podporu CodeDOM pomocí implementace <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  <xref:System.ComponentModel.Design.IComponentChangeService> tříd a.

Další informace o psaní návrháře pomocí .NET Framework najdete v tématu věnovaném [podpoře podpory Design-Time](/previous-versions/37899azc(v=vs.140)).

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Poskytuje výchozí infrastrukturu pro vrácení zpět podle:

- Poskytování implementací pro vrácení zpět <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> prostřednictvím <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> tříd a.

- Dodávání Persistence a podpora CodeDOM prostřednictvím výchozích <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> a <xref:System.ComponentModel.Design.IComponentChangeService> implementací.

## <a name="obtain-undo-support-automatically"></a>Získat podporu pro vrácení zpět automaticky

Libovolný Návrhář vytvořený v aplikaci Visual Studio má podporu automatického a úplného vrácení zpět, pokud je, Návrhář:

- Využívá <xref:System.Windows.Forms.Control> třídu založenou na svém uživatelském rozhraní.

- Využívá standardní generování a analýzu kódu založené na CodeDOM pro generování kódu a trvalost.

   Další informace o práci s podporou CodeDOM sady Visual Studio naleznete v tématu [dynamické generování a kompilace zdrojového kódu](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Kdy použít explicitní podporu pro vrácení návrháře
 Aby návrháři používali grafické uživatelské rozhraní, které je označováno jako adaptér zobrazení, jiné než ten, který poskytuje, musí vytvořit vlastní správu zpět <xref:System.Windows.Forms.Control> .

 Příkladem může být vytvoření produktu s webovým grafickým návrhovým rozhraním, nikoli .NET Framework grafické rozhraní založené na.

 V takových případech by jeden musel zaregistrovat tento adaptér zobrazení v sadě Visual Studio pomocí <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> a poskytnout explicitní správu zpět.

 Aby návrháři nepoužívali model generování kódu sady Visual Studio, který je k dispozici v oboru názvů, je nutné poskytnout podporu CodeDOM a trvalosti <xref:System.CodeDom> .

## <a name="undo-support-features-of-the-designer"></a>Vrátit funkce podpory v Návrháři
 Sada SDK prostředí poskytuje výchozí implementaci rozhraní, která jsou nutná k zajištění podpory pro vrácení zpět, kterou mohou používat návrháři, kteří nepoužívají <xref:System.Windows.Forms.Control> třídy založené na jejich uživatelských rozhraních nebo standardní model CodeDOM a trvalost.

 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Třída je odvozena z .NET Framework <xref:System.ComponentModel.Design.UndoEngine> třídy pomocí implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> třídy pro správu operací vrácení zpět.

 Visual Studio poskytuje následující funkci pro vrácení návrháře zpět:

- Propojené funkce zrušení napříč několika návrháři.

- Podřízené jednotky v Návrháři mohou komunikovat s jejich rodičem implementací <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> on <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

Sada SDK prostředí poskytuje podporu CodeDOM a trvalosti tím, že poskytuje:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> jako implementace <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- A <xref:System.ComponentModel.Design.IComponentChangeService> poskytnutý hostitelem pro návrh sady Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Použití funkcí sady SDK pro prostředí k poskytnutí podpory pro vrácení zpět

Chcete-li získat podporu pro vrácení zpět, objekt implementující návrháře musí vytvořit instanci a inicializovat instanci <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> třídy s platnou <xref:System.IServiceProvider> implementací. Tato <xref:System.IServiceProvider> Třída musí poskytovat následující služby:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Návrháři pomocí serializace CodeDOM sady Visual Studio se mohou rozhodnout použít <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] jako implementaci rozhraní <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   V tomto případě <xref:System.IServiceProvider> by třída poskytnutá <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> konstruktoru měla vracet tento objekt jako implementaci <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> třídy.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Návrháři, kteří používají výchozí hodnoty <xref:System.ComponentModel.Design.DesignSurface> poskytované hostitelem pro návrh sady Visual Studio, mají zaručenou výchozí implementaci <xref:System.ComponentModel.Design.IComponentChangeService> třídy.

Návrháři implementující <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mechanismus vrácení zpět automaticky sledují změny, pokud:

- Změny vlastností se provádí prostřednictvím <xref:System.ComponentModel.TypeDescriptor> objektu.

- <xref:System.ComponentModel.Design.IComponentChangeService> události jsou generovány ručně, pokud je potvrzena zpětná změna.

- Změny v Návrháři byly vytvořeny v kontextu <xref:System.ComponentModel.Design.DesignerTransaction> .

- Návrhář rozhodne explicitně vytvořit jednotky akcí zpět pomocí standardní jednotky pro vrácení zpět, která je poskytována implementací <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> nebo implementací specifickou pro sadu Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , která je odvozena z <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> a také poskytuje implementaci obou <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Rozšiřování podpory Design-Time](/previous-versions/37899azc(v=vs.140))
