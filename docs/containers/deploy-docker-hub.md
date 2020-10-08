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
monikerRange: '>=vs-2019'
ms.openlocfilehash: 5bbdbffa9de9ac7789495249d3e7bfb0a8d65377
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2020
ms.locfileid: "91829899"
---
# <a name="deploy-to-docker-hub"></a>Nasazení do Docker Hubu

Docker Hub poskytuje pohodlný hostující službu pro vaše úložiště imagí. V aplikaci Visual Studio můžete snadno nasazovat do Docker Hub ručně.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Vytvoření účtu Docker a úložiště Docker Hub

[Zaregistrujte](https://hub.docker.com/signup) si účet Docker, pokud ho ještě nemáte.

Pokud nemáte úložiště Docker Hub, vytvořte ho v [Dock hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publikování obrázku jednoho projektu do Docker Hub

1. Klikněte pravým tlačítkem na uzel projektu a vyberte **publikovat...**. Zobrazí se obrazovka se zobrazenými možnostmi nasazení.

   ![Snímek obrazovky s možnostmi nasazení](media/container-tools/vs-2019/docker-container-registry.png)

1. Zvolte **docker Container Registry**a pak zvolte **Docker Hub**.

   ![Snímek obrazovky dialogového okna pro publikování – výběr centra Docker](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Zadejte svoje přihlašovací údaje Docker.

   ![Snímek obrazovky s dialogovým oknem Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Pokud se připojujete k vlastnímu úložišti (ne k organizaci), ponechte zaškrtnuté políčko **publikovat do osobního úložiště** . Pokud je úložiště vlastněno organizací, zrušte zaškrtnutí políčka a zadejte název organizace. Zadejte uživatelské jméno a heslo Docker pro účet Docker, který má oprávnění pro přístup k úložišti, ke kterému se připojujete, a pak vyberte **Uložit**.

   Visual Studio se pokusí nasadit vaši image do Docker Hub.  V případě úspěchu se obrazovka **publikování** zobrazí s adresou URL pro Image úložiště, značkou image, úložištěm a konfigurací sestavení (například **vydání**).

   ![Snímek obrazovky pro publikování](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Bitovou kopii můžete kdykoli aktualizovat kliknutím na tlačítko **publikovat** na této stránce.  Nebo můžete profil upravit nebo odebrat pomocí odkazů pod adresou URL.

## <a name="next-steps"></a>Další kroky

Publikování do [Azure Container Registry](/azure/container-registry/) podle kroků uvedených v části [nasazení na Azure Container Registry](hosting-web-apps-in-docker.md).

Pomocí [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true)nastavte průběžnou integraci a doručování (CI/CD).

## <a name="see-also"></a>Viz také

[Nasadit do Azure App Service](deploy-app-service.md) 
 [Nástroje kontejneru sady Visual Studio](./index.yml).