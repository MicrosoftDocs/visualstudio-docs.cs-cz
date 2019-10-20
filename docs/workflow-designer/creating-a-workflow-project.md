---
title: Vytvoření projektu modelu Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f793e6ff468bdec6df499c5e5eb6b8524e9e4d5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650577"
---
# <a name="workflow-project-templates"></a>Šablony projektu pracovního postupu

Pomocí šablon projektů sady Visual Studio můžete vytvářet pracovní postupy, služby pracovních postupů Windows Communication Foundation (WCF), vlastní aktivity a návrháře vlastních aktivit. Tento článek popisuje, jak vytvořit knihovny a aplikace pomocí šablon projektů, které jsou k dispozici v aplikaci Visual Studio.

## <a name="create-a-workflow-project"></a>Vytvoření projektu pracovního postupu

Visual Studio nabízí čtyři různé šablony projektu pracovního postupu:

- Konzolová aplikace pracovního postupu

- Aplikace služby pracovního postupu WCF

- Knihovna aktivit

- Knihovna návrháře aktivit

Chcete-li získat přístup k těmto šablonám, nejprve nainstalujte **programovací model Windows Workflow Foundation** komponentu sady Visual Studio. Podrobné pokyny najdete v tématu [instalace programovací model Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Po instalaci součásti **programovací model Windows Workflow Foundation** vyberte **soubor**  > **Nový**  > **projekt**.

1. Vyhledejte a vyberte šablonu projektu pracovního postupu, například šablonu **konzolové aplikace pracovního postupu** .

1. Pokračujte v vytváření projektu.

   > [!NOTE]
   > Pokud chcete přidat nový projekt do existujícího řešení, otevřete toto řešení v aplikaci Visual Studio, klikněte pravým tlačítkem na řešení v **Průzkumník řešení**a vyberte **Přidat**  > **Nový projekt**.

## <a name="workflow-console-app"></a>Konzolová aplikace pracovního postupu

Pokud zvolíte šablonu **konzolové aplikace pracovního postupu** , Visual Studio vytvoří definici pracovního postupu v jazyce XAML. Návrhář postupu provádění se otevře a zobrazí plátno pro pracovní postup, který jste vytvořili. Chcete-li vytvořit pracovní postup, přetáhněte aktivity nebo jiné položky pracovního postupu ze **sady nástrojů** na návrhovou plochu.

## <a name="wcf-workflow-service-app"></a>Aplikace služby pracovního postupu WCF

Pokud zvolíte šablonu **aplikace služby pracovního postupu WCF** , Visual Studio vytvoří definici služby jako XAML. Návrhář postupu provádění se otevře v zobrazení Návrh s aktivitou <xref:System.Activities.Statements.Sequence>, která obsahuje sadu <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivit.

## <a name="activity-library"></a>Knihovna aktivit

Pokud zvolíte šablonu **knihovny aktivit** , aplikace Visual Studio vytvoří definici aktivity v jazyce XAML. Návrhář postupu provádění se otevře a zobrazí plátno pro vaši vlastní aktivitu. Přetáhněte aktivitu ze **sady nástrojů** na návrhovou plochu, aby byla zahrnuta do vlastní aktivity.

> [!NOTE]
> V těle vlastní aktivity máte povolenou jenom jednu podřízenou aktivitu. Tato podřízená aktivita ale může být složená aktivita, například aktivita <xref:System.Activities.Statements.Sequence> nebo aktivita <xref:System.Activities.Statements.Flowchart>.

## <a name="activity-designer-library"></a>Knihovna návrháře aktivit

Pokud zvolíte šablonu **knihovny návrháře aktivit** , aplikace Visual Studio vytvoří definici návrháře aktivit v jazyce XAML a implementační soubor s kódem na pozadí. Návrhář postupu provádění se otevře a zobrazí plátno pro návrháře aktivit. Ovládací prvky Windows Presentation Foundation (WPF) přetáhněte ze **sady nástrojů** na návrhovou plochu, aby je bylo možné použít v Návrháři vlastních aktivit.

Příklad implementace vlastního návrháře aktivit naleznete v tématu [How to: Create a Custom Activity Designer](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Vlastní návrháře aktivit lze použít pro vlastní aktivity a pro výchozí aktivity rozhraní .NET.

## <a name="see-also"></a>Viz také:

- [Použití Návrhář postupu provádění](developing-applications-with-the-workflow-designer.md)
- [Pracovní postupy návrhu (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)