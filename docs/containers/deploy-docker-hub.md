---
title: Nasazení kontejneru Docker ASP.NET Core do Docker Hub | Microsoft Docs
description: Naučte se používat nástroje sady Visual Studio Container k nasazení webové aplikace ASP.NET Core do Docker Hub.
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: f1c02e1fdc0c72ac23cb65605f324608a7fc33d7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536887"
---
# <a name="deploy-to-docker-hub"></a>Nasazení do Docker Hubu

Docker Hub poskytuje pohodlný hostující službu pro vaše úložiště imagí. V aplikaci Visual Studio můžete snadno nasazovat do Docker Hub ručně.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Vytvoření účtu Docker a úložiště Docker Hub

[Zaregistrujte](https://hub.docker.com/signup) si účet Docker, pokud ho ještě nemáte.

Pokud nemáte úložiště Docker Hub, vytvořte ho v [Dock hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publikování obrázku jednoho projektu do Docker Hub

1. Klikněte pravým tlačítkem na uzel projektu a vyberte **publikovat...**. Zobrazí se obrazovka se zobrazenými možnostmi nasazení.

   ![Snímek obrazovky s možnostmi nasazení](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. V části **Vyberte cíl publikování**zvolte možnost **Container Registry**a pak zvolte **Docker Hub**. Zobrazí se dialogové okno **centrum Docker** .

   ![Snímek obrazovky s dialogovým oknem Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Pokud se připojujete k vlastnímu úložišti (ne k organizaci), ponechte zaškrtnuté políčko **publikovat do osobního úložiště** . Pokud je úložiště vlastněno organizací, zrušte zaškrtnutí políčka a zadejte název organizace. Zadejte uživatelské jméno a heslo Docker pro účet Docker, který má oprávnění pro přístup k úložišti, ke kterému se připojujete, a pak vyberte **Uložit**.  

   Visual Studio se pokusí nasadit vaši image do Docker Hub.  V případě úspěchu se obrazovka **publikování** zobrazí s adresou URL pro Image úložiště, značkou image, úložištěm a konfigurací sestavení (například **vydání**).

   ![Snímek obrazovky pro publikování](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Bitovou kopii můžete kdykoli aktualizovat kliknutím na tlačítko **publikovat** na této stránce.  Nebo můžete profil upravit nebo odebrat pomocí odkazů pod adresou URL.

## <a name="next-steps"></a>Další kroky

Publikování do [Azure Container Registry](/azure/container-registry/) podle kroků uvedených v části [nasazení na Azure Container Registry](hosting-web-apps-in-docker.md).

Pomocí [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops)nastavte průběžnou integraci a doručování (CI/CD).

## <a name="see-also"></a>Viz také

[Nasadit do Azure App Service](deploy-app-service.md) 
 [Nástroje kontejneru sady Visual Studio](/visualstudio/containers/).