---
title: 'Postupy: nastavení příkazů nasazení služby SharePoint | Microsoft Docs'
description: Seznamte se s postupem přizpůsobení procesu nasazení nastavením předběžného nasazení SharePointu a příkazu po nasazení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 72938f316be22cd9b2eab2d7dab893c9370fb0ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965847"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Postupy: nastavení příkazů nasazení služby SharePoint
  Proces nasazení můžete přizpůsobit nastavením příkazů před nasazením a po nasazení. Tyto příkazy se spouští před a po dalších akcích nasazení při ladění řešení služby SharePoint ze sady Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Přidání příkazu před nasazením

1. Na panelu nabídek vyberte   >  **\<*ProjectName*> vlastnosti** projektu.

2. Vyberte kartu **služby SharePoint** .

3. Do textového pole **příkazový řádek před nasazením** zadejte příkazy MS-DOS nebo MSBuild pro přizpůsobení tohoto kroku.

     Pokud například chcete zobrazit seznam obsahu adresáře před dokončením nasazení, zadejte **dir**.

### <a name="to-add-a-post-deployment-command"></a>Přidání příkazu po nasazení

1. Na panelu nabídek vyberte   >  **\<*ProjectName*> vlastnosti** projektu.

2. Vyberte kartu **služby SharePoint** .

3. Do textového pole **příkazový řádek po nasazení** zadejte příkazy MS-DOS nebo MSBuild pro přizpůsobení tohoto kroku.

     Pokud například chcete zobrazit seznam obsahu adresáře po dokončení nasazení, zadejte **dir**. Chcete-li použít proměnnou MSBuild ke zkopírování sestavení z adresáře sestavení, zadejte **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
