---
title: Přidání Mobile Services pomocí připojených služeb
description: Přidání Mobile Services pomocí dialogovém okně Visual Studio přidání připojené služby
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
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300183"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Přidání Mobile Services pomocí připojených služeb sady Visual Studio
Pomocí sady Visual Studio 2015 se můžete připojit k Azure Mobile Services pomocí dialogového okna **Přidat připojenou službu** . Můžete připojit z jakékoli klientské aplikace C#, všechny Javascriptové aplikace nebo aplikace Cordova pro různé platformy. Když se připojíte, můžete vytvořit a přístup k datům, vytvořte vlastní rozhraní API a naplánované úlohy nebo přidat podporu pro nabízená oznámení.  Operace připojené služby přidá všechny příslušné odkazy a připojovací kód. Můžete také využít výhody integrované podpory pro ověřování s řadou oblíbených schémat identity, jako je Azure AD, Facebook, Twitter a Microsoft Accounts.

## <a name="supported-project-types"></a>Podporované typy projektů
> [!NOTE]
> V sadě Visual Studio 2015 není podporováno přidávání pomocí dialogového okna připojené služby Azure Mobile Services pro projekty Windows Universal (Windows 10). Azure Mobile Services můžete přidat nainstalováním vhodné balíčky pomocí Správce balíčků NuGet pro projekt.
>
>

Dialogové okno připojené služby můžete použít pro připojení k Azure Mobile Services v následujících typech projektů.

* Projekty .NET Windows 8.1 Store, Telefon a univerzální aplikace
* Projekty jazyka JavaScript Windows 8.1 Store, Telefon a univerzální aplikace pro
* Projekty vytvořené pomocí nástrojů Visual Studio pro Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Připojení k mobilním službám Azure pomocí dialogového okna připojené služby
1. Ujistěte se, že máte účet Azure. Pokud nemáte účet Azure, můžete si zaregistrovat [bezplatnou zkušební verzi](https://go.microsoft.com/fwlink/?LinkId=518146).
2. Otevřete dialogové okno **Přidat připojené služby** .

   * V případě aplikací .NET otevřete projekt v aplikaci Visual Studio, otevřete kontextovou nabídku uzlu **odkazy** v Průzkumník řešení a pak zvolte **Přidat připojenou službu** .

        ![Připojení k mobilní služby Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * V případě Apache Cordova projektů aplikací otevřete projekt v aplikaci Visual Studio, otevřete kontextovou nabídku uzlu projektu v Průzkumník řešení a zvolte možnost **Přidat připojenou službu**.
3. V dialogovém okně **Přidat připojenou službu** zvolte **Azure Mobile Services**a pak klikněte na tlačítko **Konfigurovat** . Můžete být vyzváni k přihlášení do Azure, pokud jste tak již neučinili.

    ![Přidání mobilní služby Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. V dialogovém okně **Azure Mobile Services** vyberte existující mobilní službu, pokud ji máte. Pokud potřebujete k vytvoření nové mobilní služby Azure, postupujte podle tohoto postupu provedete to tak. Jinak přejděte k dalšímu kroku.

    Chcete-li vytvořit nový účet mobilních služeb:

   1. V dolní části dialogového okna klikněte na odkaz **vytvořit službu** .
       ![přidat novou mobilní připojenou službu](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. V dialogovém okně **vytvořit mobilní službu** můžete zvolit mobilní službu back-end JavaScriptu nebo mobilní službu back-end .NET z rozevíracího seznamu **runtime** .

       ![Vytvoření mobilní služby](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Back-end službu jazyka JavaScript je jednoduché a účinné. Pokud vytvoříte mobilní službu back-end JavaScript, kód jazyka JavaScript na straně serveru je uložen v cloudu, ale serverových skriptů můžete upravit pomocí Průzkumníku serveru nebo portálu pro správu Azure.

       Mobilní služby back-end .NET poskytuje úplné výkonná a flexibilní webové rozhraní API a Entity Framework. Pokud vytvoříte mobilní službu back-endu .NET, projekt vytvořen a přidán do řešení.
   3. Vyberte **oblast** , ve které chcete mobilní službu, a pak zadejte uživatelské jméno a heslo pro server.
   4. Po zadání všech požadovaných informací klikněte na tlačítko **vytvořit** a vytvořte tak mobilní službu.
   5. Nová mobilní služba by se měla zobrazit v seznamu služby v dialogovém okně **Azure Mobile Services** . Zvolte novou mobilní službu v seznamu a potom kliknutím na tlačítko **Přidat** přidejte službu do projektu.
5. Zkontrolujte na stránce Začínáme, který se zobrazí a zjistěte, jak se váš projekt změnil. Pokaždé, když přidáte připojenou službu ve vašem prohlížeči zobrazí stránku Začínáme. Můžete zkontrolovat další navrhované kroky a příklady kódu, nebo přepněte na stránku co se stalo a podívejte se, jaké odkazy byly přidány do projektu a jak váš kód a konfigurační soubory byly změněny.
6. Pomocí ukázky kódu a jako vodítko, začněte psát kód pro přístup k mobilní službě.

## <a name="how-your-project-is-modified"></a>Jak se váš projekt změnil
Jak Visual Studio změní projekt, závisí na typu projektu. Pro C# klientské aplikace si přečtěte téma [co C# se stalo – projekty](https://go.microsoft.com/fwlink/p/?LinkId=513119). Pro klientské aplikace JavaScriptu si přečtěte téma [co se stalo – javascriptové projekty](https://go.microsoft.com/fwlink/p/?LinkId=513120). Pro aplikace Cordova si přečtěte téma [co se stalo – projekty Cordova](https://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Další kroky
Klást otázky a nechat si pomoct:

* [Fórum MSDN: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services na blogu týmu Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Mobile Services Azure na adrese azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Dokumentace ke službě Azure Mobile Services na adrese azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
