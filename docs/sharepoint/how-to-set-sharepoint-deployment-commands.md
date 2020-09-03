---
title: 'Postupy: nastavení příkazů nasazení služby SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c2329efef64e7d8605f8483ff7dce3107cd702fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015509"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Postupy: nastavení příkazů nasazení služby SharePoint
  Proces nasazení můžete přizpůsobit nastavením příkazů před nasazením a po nasazení. Tyto příkazy se spouští před a po dalších akcích nasazení při ladění řešení služby SharePoint ze sady Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Přidání příkazu před nasazením

1. Na panelu nabídek vyberte **Project**  >  ** \<*ProjectName*> vlastnosti**projektu.

2. Vyberte kartu **služby SharePoint** .

3. Do textového pole **příkazový řádek před nasazením** zadejte příkazy MS-DOS nebo MSBuild pro přizpůsobení tohoto kroku.

     Pokud například chcete zobrazit seznam obsahu adresáře před dokončením nasazení, zadejte **dir**.

### <a name="to-add-a-post-deployment-command"></a>Přidání příkazu po nasazení

1. Na panelu nabídek vyberte **Project**  >  ** \<*ProjectName*> vlastnosti**projektu.

2. Vyberte kartu **služby SharePoint** .

3. Do textového pole **příkazový řádek po nasazení** zadejte příkazy MS-DOS nebo MSBuild pro přizpůsobení tohoto kroku.

     Pokud například chcete zobrazit seznam obsahu adresáře po dokončení nasazení, zadejte **dir**. Chcete-li použít proměnnou MSBuild ke zkopírování sestavení z adresáře sestavení, zadejte **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
