---
title: Publikování do Azure App Service
ms.date: 01/17/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 49a8dfb3625ebda01caf0d0fa806b197c1bdaefb
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722994"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Publikování webové aplikace pro Azure App Service pomocí Visual Studio pro Mac

K publikování ASP.NET Corech aplikací do Azure App Service můžete použít nástroj pro publikování.

## <a name="prerequisites"></a>Požadavky

- Je nainstalována [aplikace Visual Studio 2017 pro systém Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) s povoleným ASP.NET Core.
- Předplatné Azure. Pokud ještě předplatné nemáte, [Zaregistrujte se zdarma](https://azure.microsoft.com/free/dotnet/), včetně $200 na kreditu po dobu 30 dnů a 12 měsíců oblíbených bezplatných služeb.
- ASP.NET Core projekt. Pokud projekt ještě nemáte, můžete [vytvořit nový](./create-new-projects.md?view=vsmac-2017&preserve-view=true).

## <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

 1. V Oblast řešení klikněte pravým tlačítkem myši na projekt a vyberte možnost **publikovat**.

    ![Místní nabídka publikovat](media/publish-context-menu.png)

 2. Pokud jste tento projekt publikovali již dříve Azure App Service, zobrazí se v nabídce profil publikování. Kliknutím na tento profil publikování spusťte proces publikování.

 3. Pokud chcete tento projekt publikovat, aby se App Service poprvé, vyberte **publikovat do Azure** .

    ![Místní nabídka publikovat do App Service](media/publish-to-azure-context-menu.png)

 4. Zobrazí se dialogové okno **publikovat do Azure App Service** a zobrazí se všechny existující App Services. Chcete-li publikovat na existující App Service, vyberte App Service v seznamu a klikněte na tlačítko **publikovat**.

    ![Dialog publikovat do Azure App Service](media/publish-to-app-service-dialog.png)

 5. Pokud chcete vytvořit nový App Service, klikněte na tlačítko **Nový** .

    ![Dialog publikovat do App Service](media/publish-to-app-service-dialog-new-selected.png)

 6. Zobrazí se dialogové okno **nový App Service** . V tomto dialogovém okně můžete nakonfigurovat nastavení pro nové App Service.

    ![Dialog Nový App Service](media/publish-new-app-service.png)

    Existuje několik možností, jak zvážit přizpůsobení. Název App Service bude ve výchozím nastavení název projektu. Pokud není název k dispozici, zobrazí se na pravé straně vstupního pole symbol upozornění. Název App Service bude použit v adrese URL vašeho webu, takže název musí být platný pro použití v adrese URL.

    Předplatné, ke kterému se App Service přidruží, můžete změnit pomocí rozevírací nabídky **předplatné** .

    Pomocí rozevíracího seznamu můžete vybrat existující **skupinu prostředků** , nebo můžete vytvořit novou pomocí **+** tlačítka.

    U App Serviceho plánu vyberte existující přepínač, nebo vytvořte nový. tím, že vyberete **vlastní** přepínač.

    Pokud chcete vytvořit nový App Service a projekt do něj publikovat, klikněte na **vytvořit**.

    Po kliknutí na tlačítko **vytvořit** **nový dialog App Service** bude zavřen a měla by se zobrazit následující zpráva oznamující, že vytváření App Service bylo spuštěno.

      ![Vytvořit App Serviceovou zprávu](media/publish-create-app-service-message.png)

    Po kliknutí na tlačítko **OK** se zpráva zavře a můžete pokračovat v práci na projektu. Stav procesu publikování můžete sledovat na stavovém řádku v horní části rozhraní IDE. Po úspěšném publikování webové aplikace se web otevře ve výchozím prohlížeči.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]