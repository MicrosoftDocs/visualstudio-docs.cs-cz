---
title: Vytvoření projektu modelu Workflow Foundation
description: Naučte se vytvářet knihovny a aplikace pomocí šablon projektů, které jsou k dispozici v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf8c0fe0b716cecee19c00bb0b300d4ffdc99355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894358"
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

1. Po instalaci součásti **programovací model Windows Workflow Foundation** vyberte **soubor**  >  **Nový**  >  **projekt**.

1. Vyhledejte a vyberte šablonu projektu pracovního postupu, například šablonu **konzolové aplikace pracovního postupu** .

1. Pokračujte v vytváření projektu.

   > [!NOTE]
   > Chcete-li přidat nový projekt do existujícího řešení, otevřete toto řešení v aplikaci Visual Studio, klikněte pravým tlačítkem myši na řešení v **Průzkumník řešení** a vyberte možnost **Přidat**  >  **Nový projekt**.

## <a name="workflow-console-app"></a>Konzolová aplikace pracovního postupu

Pokud zvolíte šablonu **konzolové aplikace pracovního postupu** , Visual Studio vytvoří definici pracovního postupu v jazyce XAML. Návrhář postupu provádění se otevře a zobrazí plátno pro pracovní postup, který jste vytvořili. Chcete-li vytvořit pracovní postup, přetáhněte aktivity nebo jiné položky pracovního postupu ze **sady nástrojů** na návrhovou plochu.

## <a name="wcf-workflow-service-app"></a>Aplikace služby pracovního postupu WCF

Pokud zvolíte šablonu **aplikace služby pracovního postupu WCF** , Visual Studio vytvoří definici služby jako XAML. Návrhář postupu provádění se otevře v zobrazení Návrh s <xref:System.Activities.Statements.Sequence> aktivitou, která obsahuje sadu <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> aktivit a.

## <a name="activity-library"></a>Knihovna aktivit

Pokud zvolíte šablonu **knihovny aktivit** , aplikace Visual Studio vytvoří definici aktivity v jazyce XAML. Návrhář postupu provádění se otevře a zobrazí plátno pro vaši vlastní aktivitu. Přetáhněte aktivitu ze **sady nástrojů** na návrhovou plochu, aby byla zahrnuta do vlastní aktivity.

> [!NOTE]
> V těle vlastní aktivity máte povolenou jenom jednu podřízenou aktivitu. Tato podřízená aktivita však může být složenou aktivitou, například <xref:System.Activities.Statements.Sequence> aktivitou nebo <xref:System.Activities.Statements.Flowchart> aktivitou.

## <a name="activity-designer-library"></a>Knihovna návrháře aktivit

Pokud zvolíte šablonu **knihovny návrháře aktivit** , aplikace Visual Studio vytvoří definici návrháře aktivit v jazyce XAML a implementační soubor s kódem na pozadí. Návrhář postupu provádění se otevře a zobrazí plátno pro návrháře aktivit. Ovládací prvky Windows Presentation Foundation (WPF) přetáhněte ze **sady nástrojů** na návrhovou plochu, aby je bylo možné použít v Návrháři vlastních aktivit.

Příklad implementace vlastního návrháře aktivit naleznete v tématu [How to: Create a Custom Activity Designer](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Vlastní návrháře aktivit lze použít pro vlastní aktivity a pro výchozí aktivity rozhraní .NET.

## <a name="see-also"></a>Viz také

- [Používání návrháře postupu provádění](developing-applications-with-the-workflow-designer.md)
- [Pracovní postupy návrhu (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
