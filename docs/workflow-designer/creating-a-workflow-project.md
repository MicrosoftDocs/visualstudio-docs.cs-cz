---
title: Vytvoření projektu Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a4f8ed1effbc459bd2a17e3433738c1b461513b
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755651"
---
# <a name="workflow-project-templates"></a>Pracovní postup šablony projektů

Pracovní postupy, pracovní postup služby Windows Communication Foundation (WCF), vlastní aktivity a Návrháře vlastních aktivit můžete vytvořit pomocí šablony projektů Visual Studio. Tento článek popisuje postup vytváření knihoven a aplikace se šablonami projektů, která je k dispozici v sadě Visual Studio.

## <a name="create-a-workflow-project"></a>Vytvořit projekt Workflow

Visual Studio poskytuje čtyři různé šablony projektu pracovního postupu:

- Pracovní postup konzolové aplikace

- Aplikace služby pracovního postupu WCF

- Knihovna aktivit

- Knihovna návrháře aktivit

Chcete-li získat přístup k tyto šablony, nejprve nainstalovat **modelu Windows Workflow Foundation** součást produktu Visual Studio 2017. Podrobné pokyny najdete v tématu [nainstalovat Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Po instalaci **modelu Windows Workflow Foundation** součást, otevřete **nový projekt** dialogové okno výběrem **soubor** > **nový**  >  **Projektu**.

1. V levém podokně, vyberte **Visual C#** > **pracovního postupu** kategorie (nebo **jazyka Visual Basic** > **pracovního postupu**Pokud dáváte přednost jazyka Visual Basic).

1. V prostředním podokně, vyberte šablonu projektu **pracovního postupu konzolové aplikace**.

1. V **název** zadejte popisný název pro svůj projekt, aby bylo snadné identifikovat.

1. V **umístění** zadejte adresář, ve kterém chcete uložit projektu, nebo vyberte **Procházet** přejděte k němu.

1. V **řešení** pole, zadejte název nové řešení. Vyberte **OK** k vytvoření aplikace.

   > [!NOTE]
   > Pokud chcete přidat nový projekt do existujícího řešení, otevřete toto řešení v sadě Visual Studio, klikněte pravým tlačítkem na řešení v **Průzkumníku řešení**a vyberte **přidat** > **nový Projekt** otevřete **nový projekt** dialogové okno.

## <a name="workflow-console-app"></a>Pracovní postup konzolové aplikace

Pokud se rozhodnete **pracovního postupu konzolové aplikace** šablony sady Visual Studio vytvoří definici pracovního postupu v jazyce XAML. Návrhář postupu provádění se zobrazí na plátno pro pracovní postup, který jste vytvořili. Chcete-li vytvořit pracovní postup, přetáhněte aktivity nebo jiné položky pracovního postupu z **sada nástrojů** na plochu návrháře.

## <a name="wcf-workflow-service-app"></a>Aplikace služby pracovního postupu WCF

Pokud se rozhodnete **aplikace služby pracovního postupu WCF** šablony sady Visual Studio vytvoří definici služby jako XAML. Návrhář postupu provádění se otevře zobrazení návrhu s <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje sadu <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity.

## <a name="activity-library"></a>Knihovna aktivit

Pokud se rozhodnete **knihovna aktivit** šablony sady Visual Studio vytvoří definici aktivity v jazyce XAML. Návrhář postupu provádění se zobrazí na plátno vlastní aktivity. Přetáhněte ji na aktivitu ze **sada nástrojů** na návrhovou plochu, která chcete zahrnout do vlastní aktivity.

> [!NOTE]
> Máte oprávnění pouze jednu podřízenou aktivitu v těle vlastní aktivity. Však podřízené aktivity může být složené aktivity, například <xref:System.Activities.Statements.Sequence> aktivity nebo <xref:System.Activities.Statements.Flowchart> aktivity.

## <a name="activity-designer-library"></a>Knihovna návrháře aktivit

Pokud se rozhodnete **knihovny návrháře aktivit** šablony sady Visual Studio vytvoří definici návrháře aktivit v XAML a soubor implementaci kódu na pozadí. Návrhář postupu provádění se zobrazí na plátno pro vaše Návrhář aktivity. Ovládací prvky přetažení Windows Presentation Foundation (WPF) z **sada nástrojů** na návrhovou plochu jejich použití v Návrháři vaše vlastní aktivity.

Příklad implementace vlastního návrháře aktivit, naleznete v části [postupy: vytvoření vlastního návrháře aktivit](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Návrháři vlastních aktivit lze použít pro vlastní aktivity a výchozí aktivity rozhraní .NET Framework.

## <a name="see-also"></a>Viz také:

- [Použití návrháře pracovních postupů](../workflow-designer/using-the-workflow-designer.md)
- [Navrhovat pracovní postupy (rozhraní .NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)