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
ms.workload:
- azure
ms.openlocfilehash: 97964589b832b05f4d528a801a1899eeb8385883
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714463"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Publikování webové aplikace do služby Azure App Service pomocí Visual Studia pro Mac

Pomocí nástroje Publikovat můžete publikovat ASP.NET základní aplikace do služby Azure App Service.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 pro Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) nainstalované s povoleným ASP.NET Core.
- Předplatné Azure. Pokud ještě nemáte předplatné, [zaregistrujte se zdarma](https://azure.microsoft.com/free/dotnet/), který zahrnuje 200 dolarů v kreditu po dobu 30 dnů a 12 měsíců populárních bezplatných služeb.
- Projekt ASP.NET Core. Pokud ještě nemáte projekt, můžete [vytvořit nový](/visualstudio/mac/create-new-projects?view=vsmac-2017).

## <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

 1. Na panelu řešení klikněte pravým tlačítkem myši na projekt a zvolte **Publikovat**.

    ![Publikovat místní nabídku](media/publish-context-menu.png)

 2. Pokud jste tento projekt dříve publikovali do služby Azure App Service, uvidíte profil publikování v nabídce. Vyberte tento profil publikování a spusťte proces publikování.

 3. Pokud chcete tento projekt poprvé publikovat ve službě App Service, vyberte **Publikovat do Azure.**

    ![Místní nabídka Publikovat do služby App Service](media/publish-to-azure-context-menu.png)

 4. Zobrazí se dialogové okno **Publikovat do služby Azure App Service** a zobrazí se všechny existující služby App Services. Pokud chcete publikovat v existující službě App Service, vyberte v seznamu službu App Service a klikněte na **Publikovat**.

    ![Dialogové okno Publikovat do služby Azure App Service](media/publish-to-app-service-dialog.png)

 5. Chcete-li vytvořit novou službu App Service, klepněte na tlačítko **Nový.**

    ![Dialogové okno Publikovat do služby Aplikace](media/publish-to-app-service-dialog-new-selected.png)

 6. Zobrazí se dialogové okno **Nová služba aplikace.** V tomto dialogovém okně můžete nakonfigurovat nastavení nové služby App Service.

    ![Dialogové okno Nová služba aplikace](media/publish-new-app-service.png)

    Existuje několik možností, jak zvážit přizpůsobení zde. Název služby App Service bude ve výchozím nastavení název projektu. Pokud název není k dispozici, zobrazí se na pravé straně vstupního pole výstražné znaménko. Název služby App Service bude použit v adrese URL vašeho webu, takže název musí být platný pro použití v adrese URL.

    Můžete změnit předplatné, ke kterému bude appslužba přidružena, pomocí rozevíracího **nabídky Předplatného.**

    Pomocí rozevíracího přehledu můžete vybrat existující **skupinu prostředků** **+** nebo můžete pomocí tlačítka vytvořit novou skupinu.

    Pro plán Služby App Service vyberte existující nebo vytvořte nový výběrem **vlastního** přepínacího tlačítka.

    Pokud chcete vytvořit novou službu App Service a publikovat do ní projekt, klikněte na **Vytvořit**.

    Po kliknutí na **tlačítko Vytvořit** **novou službu aplikace** dialogové okno bude zamítnuta a měli byste vidět následující zprávu oznamující, že vytvoření služby App Service byla spuštěna.

      ![Vytvořit zprávu služby App Service](media/publish-create-app-service-message.png)

    Po kliknutí na **tlačítko OK** je zpráva odmítnuta a můžete pokračovat v práci na projektu. Můžete sledovat stav procesu publikování se stavovým panelem v horní části ide. Po úspěšném publikování webové aplikace se web otevře s výchozím prohlížečem.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]
