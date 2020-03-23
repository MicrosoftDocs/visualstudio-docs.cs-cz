---
title: Práce s několika uživatelskými účty
ms.date: 07/23/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 872089158b6e4dc0b55c26ad187e3b68d0501f26
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027598"
---
# <a name="work-with-multiple-user-accounts"></a>Práce s několika uživatelskými účty

Pokud máte více účtů Microsoft nebo pracovnínebo školní účty, můžete je všechny přidat do sady Visual Studio, abyste měli přístup k prostředkům z libovolného účtu, aniž byste se k němu museli přihlašovat samostatně. Azure, Application Insights, Azure DevOps a služby Office 365 podporují zjednodušené přihlašovací prostředí.

Po přidání více účtů na jednom počítači, tato sada účtů přecvačit s vámi, pokud se přihlásíte do sady Visual Studio na jiném počítači.

> [!NOTE]
> Přestože názvy účtů se toulají, pověření nikoli. Při prvním pokusu o použití jejich prostředků v novém počítači budete vyzváni k zadání přihlašovacích údajů pro tyto ostatní účty.

Tento článek ukazuje, jak přidat více účtů do sady Visual Studio. Také ukazuje, jak zobrazit prostředky přístupné z těchto účtů v místech, jako je například dialogové okno **Přidat připojenou službu,** **Průzkumník serveru**a **Průzkumník týmu**.

## <a name="sign-in-to-visual-studio"></a>Přihlášení k sadě Visual Studio

Přihlaste se k Visual Studiu pomocí účtu Microsoft nebo účtu organizace. V horním rohu okna byste měli vidět, že se vaše uživatelské jméno zobrazí podobně jako toto:

![Aktuálně přihlášený uživatel](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Přístup k účtu Azure v Průzkumníkovi serveru

Chcete-li otevřít Průzkumníka serveru, zvolte **Zobrazit** > **Průzkumníka serveru** (nebo pokud používáte nastavení [prostředí](../ide/environment-settings.md)Obecné , stiskněte **kombinaci kláves Ctrl**+**Alt**+**S**). Rozbalte uzel **Azure** a všimněte si, že obsahuje prostředky dostupné v účtu Azure, který je přidružený k účtu, který jste použili k přihlášení k Visual Studiu. Vypadá podobně jako na následujícím obrázku:

![Průzkumník serveru s rozbaleným uzlovým uzlem Azure](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Při prvním použití sady Visual Studio na jakémkoli konkrétním zařízení se v dialogovém okně zobrazí pouze předplatná zaregistrovaná pod účtem, se kterým jste se přihlásili. K prostředkům pro všechny ostatní účty můžete přistupovat přímo z **Průzkumníka serveru** kliknutím pravým tlačítkem myši na uzel **Azure,** výběrem **spravovat a filtrovat předplatná**a přidáním účtů z ovládacího prvku výběru účtů. V případě potřeby pak můžete zvolit jiný účet kliknutím na šipku dolů a výběrem ze seznamu účtů. Po výběru účtu můžete přizpůsobit, která předplatná v rámci tohoto účtu se mají zobrazit v **Průzkumníkovi serveru**.

![Dialogové okno Spravovat předplatná Azure](../ide/media/vs2015_manage_subs.png)

Při příštím spuštění **Průzkumníka serveru**se zobrazí prostředky pro toto předplatné.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Přístup k účtu Azure pomocí dialogového okna Přidat připojenou službu

1. Otevřete existující projekt nebo vytvořte nový projekt.

1. V Průzkumníku **řešení**zvolte uzel projektu a potom klepněte pravým tlačítkem myši a zvolte **Přidat** > **připojenou službu**.

   Zobrazí se Průvodce **přidáním připojené služby** a zobrazí seznam služeb v účtu Azure, který je přidružený k vašemu účtu přizpůsobení sady Visual Studio. Do Azure se nemusíte přihlašovat samostatně. Je však nutné přihlásit se k ostatním účtům při prvním pokusu o přístup k jejich prostředkům z jiného počítače.

### <a name="access-azure-active-directory-in-a-web-project"></a>Přístup k Azure Active Directory ve webovém projektu

Azure Active Directory (AAD) umožňuje podporu pro koncovéuživatele jednotné přihlášení v ASP.NET MVC webové aplikace nebo ověřování AD ve službách webového rozhraní API. Ověřování domény se liší od ověřování jednotlivých uživatelských účtů. Uživatelé, kteří mají přístup k vaší doméně služby Active Directory, se mohou k webovým aplikacím připojit pomocí svých stávajících účtů AAD. Aplikace Office 365 můžou taky používat ověřování domény.

::: moniker range="vs-2017"

Chcete-li to zobrazit v akci, vytvořte nový **projekt ASP.NET základní webové aplikace.** V dialogovém okně **Nová ASP.NET základní webová aplikace** zvolte šablonu webové **aplikace** a pak zvolte **Změnit ověřování**.

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li to zobrazit v akci, vytvořte nový **projekt ASP.NET základní webové aplikace.** Na stránce **Vytvořit novou ASP.NET základní webovou aplikaci** zvolte šablonu webové **aplikace** a pak v části **Ověřování**zvolte **Změnit** .

::: moniker-end

Zobrazí se dialogové okno **Změnit ověřování,** kde můžete zvolit, jaký druh ověřování se má ve vaší aplikaci použít.

![Dialogové okno Změnit ověřování pro ASP.NET](../ide/media/vs2015_change_authentication.png)

Další informace o různých typech ověřování v ASP.NET naleznete v tématu [Vytvoření ASP.NET webových projektů v sadě Visual Studio](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Přístup k organizaci Azure DevOps

V hlavní nabídce zvolte Správa**připojení** **týmem** > a otevřete okno **Průzkumník týmu – připojení.** Zvolte **Spravovat připojení** > **připojit k projektu**. V **dialogovém** okně Připojit k projektu vyberte projekt ze seznamu (nebo vyberte **Přidat server TFS** a zadejte adresu URL serveru). Když vyberete adresu URL, budete přihlášeni, aniž byste museli znovu zadávat své přihlašovací údaje.

Další informace naleznete [v tématu Připojení k projektům v Průzkumníkovi týmu](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Přidání dalšího účtu do sady Visual Studio

Přidání dalšího účtu do sady Visual Studio:

1. Zvolte**Nastavení účtu** **souboru** > .

1. V části **Všechny účty**zvolte **Přidat účet**.

1. Na stránce **Přihlásit se ke svému účtu** vyberte účet nebo zvolte Použít jiný **účet**. Podle pokynů zadejte nová pověření účtu.

(Nepovinné) Teď můžete přejít na **Průzkumníka serveru** a zobrazit služby Azure přidružené k účtu, který jste právě přidali. V **Průzkumníkovi serveru**klikněte pravým tlačítkem myši na uzel **Azure** a zvolte Spravovat **a filtrovat předplatná**. Vyberte nový účet kliknutím na šipku rozevíracího seznamu vedle aktuálního účtu a pak zvolte, která předplatná chcete zobrazit v **Průzkumníkovi serveru**. Měli byste vidět všechny služby přidružené k zadanému předplatnému. I když nejste aktuálně přihlášeni k sadě Visual Studio pomocí druhého účtu, jste přihlášeni ke službám a prostředkům tohoto účtu. Totéž platí pro **projekt** > **Přidat připojenou službu** a **Team** > **Connect na Team Foundation Server**.

### <a name="add-an-account-using-device-code-flow"></a>Přidání účtu pomocí toku kódu zařízení

V některých případech se nemůžete přihlásit nebo přidat účet běžným způsobem. K tomu může dojít, pokud je aplikace Internet Explorer z nějakého důvodu blokována nebo pokud je síť za bránou firewall. Chcete-li tento úkol vyřešit, můžete povolit *tok kódu zařízení* přidat účet nebo znovu ověřit svůj účet. Tok kódu zařízení umožňuje přihlásit pomocí jiného&mdash;prohlížeče nebo na jiném počítači fyzické nebo virtuální (VM).

Přihlášení pomocí toku kódu zařízení:

1. Otevřete stránku [**Účty**](reference/accounts-environment-options-dialog-box.md) v části**Prostředí****možností** >  **nástrojů** > a **při přidávání nebo opětovném ověřování účtu**vyberte Povolit tok kódu zařízení . Chcete-li zavřít stránky voleb, zvolte **OK.**

1. Zvolte**Nastavení účtu** **souboru** > a otevřete stránku správy účtu.

1. V části **Všechny účty** **zvolte Přidat účet** .

   V dialogovém okně se zobrazí adresa URL a kód, který chcete vložit do webového prohlížeče.

   ![Adresa URL a kód toku kódu zařízení](media/work-with-multiple-user-accounts/device-login-code.png)

1. Stisknutím **klávesy Ctrl**+**C** zkopírujte text dialogového okna a pak zvolte **OK,** chcete-li dialog zavřít. Vložte zkopírovaný text do textového editoru, například poznámkový blok. To usnadňuje kopírování kódu v dalším kroku.

1. Přejděte na přihlašovací adresu URL zařízení v počítači nebo webovém prohlížeči, který chcete použít k přihlášení k sadě Visual Studio, a vložte nebo zadejte kód, který jste zkopírovali, do pole s textem **Kód**.

   Název aplikace **Visual Studio** by se měl na stránce zobrazit dále.

1. V části **Visual Studio**zvolte **Pokračovat**.

   ![device-login-page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Podle pokynů zadejte přihlašovací údaje svého účtu.

   Zobrazí se stránka s oznámením, že jste se v zařízení přihlásili do sady Visual Studio a že můžete zavřít okno prohlížeče.

   ![Přihlášení visual studia prostřednictvím prohlížeče dokončeno](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Vraťte se na stránku správy účtu ve Visual Studiu a uvidíte nově přidaný účet uvedený v části **Všechny účty**. Zvolte **Zavřít**.

## <a name="see-also"></a>Viz také

- [Přihlášení k sadě Visual Studio](signing-in-to-visual-studio.md)
- [Přihlášení k Visual Studiu pro Mac](/visualstudio/mac/signing-in)
