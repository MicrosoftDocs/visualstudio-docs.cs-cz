---
title: Nasazení kontejneru ASP.NET Core Dockeru do Centra Dockeru | Dokumenty společnosti Microsoft
description: Přečtěte si, jak pomocí nástrojů kontejnerů Sady Visual Studio nasadit webovou aplikaci ASP.NET Core do Centra Dockeru.
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: b033825bbe8facbeae3dcdee6a5b563461921522
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188745"
---
# <a name="deploy-to-docker-hub"></a>Nasazení do Docker Hubu

Docker Hub poskytuje pohodlnou hostingovou službu pro úložiště obrázků. Do Docker Hubu můžete snadno nasadit ručně z Visual Studia.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Vytvoření účtu Dockeru a úložiště Docker Hubu

Pokud ještě nemáte účet Dockeru, [zaregistrujte](https://hub.docker.com/signup) si účet Dockeru.

Pokud nemáte úložiště Docker Hub, vytvořte ho v [Docker Hubu](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publikování bitové kopie pro jeden projekt do Docker Hubu

1. Klikněte pravým tlačítkem myši na uzel projektu a zvolte **Publikovat...**. Zobrazí se obrazovka s možnostmi nasazení.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. V části **Vyberte cíl publikování**zvolte **Container Registry**a pak zvolte Docker **Hub**. Zobrazí se dialogové okno **Centra Dockeru.**

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Pokud se připojujete k vlastnímu úložišti (není součástí organizace), ponechte zaškrtnuté políčko **Publikovat na osobním úložišti.** Pokud úložiště vlastní organizace, zrušte zaškrtnutí políčka a zadejte název organizace. Zadejte své uživatelské jméno a heslo Dockeru pro svůj účet Dockeru, který má oprávnění k přístupu k úložišti, ke kterému se připojujete, a pak vyberte **Uložit**.  

   Visual Studio se pokusí nasadit image do centra Docker.  Pokud je úspěšná, zobrazí se obrazovka **Publikování** s adresou URL obrázku úložiště, značkou obrázku, úložištěm a konfigurací sestavení** (například **Release).**

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Obrázek můžete kdykoli aktualizovat kliknutím na tlačítko **Publikovat** na této stránce.  Nebo můžete upravit nebo odebrat profil pomocí odkazů pod adresou URL.

## <a name="next-steps"></a>Další kroky

Publikovat do [registru kontejnerů Azure](/azure/container-registry/) podle kroků na [nasazení do registru kontejnerů Azure](hosting-web-apps-in-docker.md).

Nastavte průběžnou integraci a doručování (CI/CD) s [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Viz také

[Nasazení do nástroje](deploy-app-service.md)
[kontejneru Visual Studio](/visualstudio/containers/)služby Azure App Service .