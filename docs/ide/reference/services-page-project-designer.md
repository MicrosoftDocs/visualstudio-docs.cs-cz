---
title: Stránka Služby, návrhář projektu
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d30d8e8ddcdc8c1fa4fe1935da1f1dedd1b18f4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593561"
---
# <a name="services-page-project-designer"></a>Stránka Služby, návrhář projektu

Klientské aplikační služby [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] poskytují zjednodušený přístup ke službám přihlášení, rolí a profilů z aplikací Windows Forms a Windows Presentation Foundation (WPF). Pomocí stránky **Služby** **návrháře projektu** můžete povolit a nakonfigurovat služby klientských aplikací pro váš projekt.

Pomocí klientských aplikačních služeb můžete pomocí centralizovaného serveru ověřovat uživatele, určit přiřazenou roli nebo role jednotlivých uživatelů a ukládat nastavení jednotlivých aplikací, která můžete sdílet v síti. Další informace naleznete [v tématu Client Application Services](/dotnet/framework/common-client-technologies/client-application-services).

Chcete-li získat přístup ke stránce **Služby,** vyberte uzel projektu v **Průzkumníku řešení**a v nabídce **Project** klepněte na **příkaz Vlastnosti.** Po zobrazení **Návrháře projektů** klikněte na kartu **Služby.**

## <a name="task-list"></a>Seznam úkolů

[Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 **Konfigurace**

Tento ovládací prvek nelze na této stránce upravovat. Popis tohoto ovládacího prvku naleznete v [tématu Kompilace stránky, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) nebo [Vytvořit stránku, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma**

Tento ovládací prvek nelze na této stránce upravovat. Popis tohoto ovládacího prvku naleznete v [tématu Kompilace stránky, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) nebo [Vytvořit stránku, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Povolení služeb klientských aplikací**

Tuto možnost vyberte, chcete-li povolit služby klientských aplikací. Chcete-li používat služby klientských aplikací, je nutné zadat umístění služeb na stránce **Služby.**

 **Použití ověřování systému Windows**

Označuje, že poskytovatel ověřování bude používat ověřování na základě systému Windows, to znamená identitu dodanou operačním systémem Windows.

 **Použití ověřování pomocí formulářů**

Označuje, že poskytovatel ověřování bude používat ověřování pomocí formulářů. To znamená, že vaše aplikace musí poskytnout uživatelské rozhraní pro přihlášení. Další informace naleznete v [tématu How to: Implement User Login with Client Application Services](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Umístění ověřovací služby**

Používá se pouze při ověřování pomocí formulářů. Určuje umístění ověřovací služby.

 **Volitelné: Zprostředkovatel pověření**

Používá se pouze při ověřování pomocí formulářů. Označuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> implementaci, kterou ověřovací služba použije k zobrazení přihlašovacího `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> dialogového okna, když `null` aplikace volá metodu a předá prázdné řetězce nebo parametry. Pokud toto pole ponecháte prázdné, musíte metodě <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> předat platné uživatelské jméno a heslo. Je nutné zadat zprostředkovatele pověření jako název typu s kvalifikací sestavení. Další informace naleznete <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> v tématu a [názvy sestavení](/dotnet/framework/app-domains/assembly-names). Ve své nejjednodušší podobě vypadá název typu s kvalifikací sestavení podobně jako v následujícím příkladu:`MyNamespace.MyLoginClass, MyAssembly`

 **Umístění služby rolí**

Určuje umístění služby rolí.

 **Umístění služby nastavení webu**

Určuje umístění služby profilu (nastavení webu).

 **Pokročilé**

Otevře [dialogové okno Upřesnit nastavení služeb](../../ide/reference/advanced-settings-for-services-dialog-box.md), které můžete použít k přepsání výchozího chování. Toto dialogové okno můžete například použít k určení databáze pro úložiště offline namísto použití místního systému souborů. Další informace naleznete v [dialogovém okně Upřesnit nastavení služeb](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Viz také

- [Klientské aplikační služby](/dotnet/framework/common-client-technologies/client-application-services)
- [Dialogové okno Pokročilé nastavení služeb](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Stránka Kompilovat, návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Stránka Sestavení, návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
