---
title: 'Postupy: Úprava konfigurace nasazení služby SharePoint | Microsoft Docs'
description: Zjistěte, jak vytvořit konfiguraci nasazení služby SharePoint nebo upravit existující konfiguraci nasazení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e64f805496d03b42ca70489bab1302ecf58b33bc
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903556"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Postupy: Úprava konfigurace nasazení služby SharePoint
  Můžete vytvořit konfiguraci nasazení nebo upravit existující konfiguraci nasazení. Můžete například spustit jeden krok nebo změnit pořadí kroků v procesu nasazení. Konfigurace nasazení možná budete chtít vytvořit nebo upravit, protože předdefinované a programově přidané konfigurace nelze změnit.

## <a name="create-a-sharepoint-deployment-configuration"></a>Vytvoření konfigurace nasazení služby SharePoint

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Vytvoření konfigurace nasazení služby SharePoint

1. V **Průzkumník řešení** zvolte projekt služby SharePoint a potom v řádku nabídek zvolte **projekt**,**vlastnosti** _ProjectName_.

2. Na kartě **SharePoint** klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat novou konfiguraci nasazení** .

3. Do textového pole **název** zadejte název konfigurace nasazení.

4. V podokně **dostupné kroky nasazení** vyberte kroky, které chcete přidat do konfigurace nasazení, klikněte na **>** tlačítko () a pak klikněte na tlačítko **OK** .

    > [!NOTE]
    > Pokud jste nakonfigurovali příkaz k předběžnému nasazení nebo příkazu po nasazení, budou se tyto kroky spouštět jenom v případě, že je přidáte do přizpůsobené konfigurace nasazení.

## <a name="change-the-active-deployment-configuration"></a>Změnit aktivní konfiguraci nasazení

#### <a name="to-change-the-active-deployment-configuration"></a>Změna aktivního nastavení nasazení

1. V **Průzkumník řešení** zvolte projekt služby SharePoint a poté v panelu nabídky zvolte možnost **Project**  >  **\<*ProjectName*> vlastnosti** projektu.

2. Vyberte kartu **služby SharePoint** .

3. V rozevíracím seznamu **aktivní konfigurace nasazení** vyberte název konfigurace nasazení, kterou chcete použít.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
