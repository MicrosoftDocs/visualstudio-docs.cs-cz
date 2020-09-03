---
title: Přidání Mobile Services pomocí připojených služeb
description: Přidání Mobile Services pomocí dialogového okna Přidat připojené služby v aplikaci Visual Studio
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 0a8f6fab3c8f30834a467e2ad98843b16a9245b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916701"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Přidání Mobile Services pomocí připojených služeb sady Visual Studio
Pomocí sady Visual Studio 2015 se můžete připojit k Azure Mobile Services pomocí dialogového okna **Přidat připojenou službu** . Můžete se připojit z libovolné klientské aplikace v jazyce C#, libovolné aplikace JavaScriptu nebo aplikace Cordova pro různé platformy. Po připojení můžete vytvořit a získat přístup k datům, vytvořit vlastní rozhraní API a naplánované úlohy nebo přidat podporu pro nabízená oznámení.  Operace připojené služby přidá všechny odpovídající odkazy a kód připojení. Můžete také využít integrovanou podporu pro ověřování s nejrůznějšími oblíbenými schématy identity, jako jsou Azure AD, Facebook, Twitter a účty Microsoft.

## <a name="supported-project-types"></a>Podporované typy projektů
> [!NOTE]
> V aplikaci Visual Studio 2015 se nepodporují přidání Azure Mobile Services do projektů univerzálního systému Windows (Windows 10) pomocí dialogu přidat připojené služby. Azure Mobile Services můžete přidat tak, že nainstalujete příslušné balíčky pomocí Správce balíčků NuGet pro váš projekt.
>
>

Pomocí dialogového okna připojené služby se můžete připojit k Azure Mobile Services v následujících typech projektů.

* Projekty .NET Windows 8.1 Store, telefony a univerzální aplikace
* JavaScript Windows 8.1 Store, telefony a projekty univerzální aplikace
* Projekty vytvořené pomocí Visual Studio Tools pro Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Připojení k Azure Mobile Services pomocí dialogového okna Přidat připojené služby
1. Ujistěte se, že máte účet Azure. Pokud účet Azure nemáte, můžete si zaregistrovat [bezplatnou zkušební verzi](https://azure.microsoft.com/pricing/free-trial/).
2. Otevřete dialogové okno **Přidat připojené služby** .

   * V případě aplikací .NET otevřete projekt v aplikaci Visual Studio, otevřete kontextovou nabídku uzlu **odkazy** v Průzkumník řešení a pak zvolte **Přidat připojenou službu** .

        ![Připojování ke službě Azure Mobile Service](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * V případě Apache Cordova projektů aplikací otevřete projekt v aplikaci Visual Studio, otevřete kontextovou nabídku uzlu projektu v Průzkumník řešení a zvolte možnost **Přidat připojenou službu**.
3. V dialogovém okně **Přidat připojenou službu** zvolte **Azure Mobile Services**a pak klikněte na tlačítko **Konfigurovat** . Pokud jste to ještě neudělali, může se zobrazit výzva k přihlášení do Azure.

    ![Přidání mobilní služby Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. V dialogovém okně **Azure Mobile Services** vyberte existující mobilní službu, pokud ji máte. Pokud potřebujete vytvořit novou mobilní službu Azure, postupujte podle níže uvedeného postupu. Jinak přejděte k dalšímu kroku.

    Vytvoření nového účtu mobilní služby:

   1. V dolní části dialogového okna klikněte na odkaz **vytvořit službu** .
       ![Přidat novou mobilní připojenou službu](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. V dialogovém okně **vytvořit mobilní službu** můžete zvolit mobilní službu back-end JavaScriptu nebo mobilní službu back-end .NET z rozevíracího seznamu **runtime** .

       ![Vytvoření mobilní služby](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Back-endové služby JavaScriptu jsou jednoduché a výkonné. Pokud vytvoříte mobilní službu back-end v jazyce JavaScript, kód JavaScriptu na straně serveru je uložený v cloudu, ale můžete upravovat serverové skripty pomocí Průzkumník serveru nebo portálu pro správu Azure.

       Mobilní služba back-endu .NET poskytuje plný výkon a flexibilitu webového rozhraní API a Entity Framework. Pokud vytvoříte mobilní službu back-end .NET, vytvoří se projekt pro vás a přidá se do vašeho řešení.
   3. Vyberte **oblast** , ve které chcete mobilní službu, a pak zadejte uživatelské jméno a heslo pro server.
   4. Po zadání všech požadovaných informací klikněte na tlačítko **vytvořit** a vytvořte tak mobilní službu.
   5. Nová mobilní služba by se měla zobrazit v seznamu služby v dialogovém okně **Azure Mobile Services** . Zvolte novou mobilní službu v seznamu a potom kliknutím na tlačítko **Přidat** přidejte službu do projektu.
5. Podívejte se na stránku Začínáme, která se zobrazí, a zjistěte, jak byl projekt změněn. V prohlížeči se zobrazí stránka Začínáme pokaždé, když přidáte připojenou službu. Můžete si prohlédnout navrhovaný další postup a příklady kódu nebo přepnout na stránku co se stalo, kde zjistíte, které odkazy byly přidány do projektu a jakým způsobem byly změněny vaše kódy a konfigurační soubory.
6. Pomocí ukázek kódu jako průvodce začněte psát kód pro přístup k mobilní službě!

## <a name="next-steps"></a>Další kroky
Položte otázky a Získejte pomoc:

* [Fórum MSDN: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services na blogu týmu Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Mobile Services Azure na adrese azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Dokumentace ke službě Azure Mobile Services na adrese azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
