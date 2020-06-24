---
title: Práce s účty, které vyžadují službu Multi-Factor Authentication
ms.date: 05/27/2020
ms.topic: conceptual
description: Naučte se používat Visual Studio s účty, které vyžadují službu Multi-Factor Authentication.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 696664aa5aa92a3e9a675df4803a3e65e3e81f36
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185614"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Jak používat Visual Studio s účty, které vyžadují Multi-Factor Authentication

Při spolupráci s externími uživateli typu Host je vhodné chránit aplikace a data pomocí zásad **podmíněného přístupu (CA)** , jako je **VÍCEFAKTOROVÉ ověřování (MFA)**.  

Po povolení budou uživatelé typu Host potřebovat k přístupu k prostředkům více než jenom uživatelské jméno a heslo a musí splňovat další požadavky na zabezpečení. Zásady vícefaktorového ověřování je možné vynucovat na úrovni tenanta, aplikace nebo jednotlivých uživatelů typu host úplně stejným způsobem, jako když se používají u členů vaší organizace. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>Jak se v prostředí sady Visual Studio ovlivňují zásady MFA?
Verze sady Visual Studio starší než 16,6 mohou mít degradované ověřování při použití s účty, které mají povolené zásady certifikační autority, jako je MFA, a jsou přidruženy ke dvěma nebo více klientům.

Tyto problémy mohou způsobit, že vaše instance aplikace Visual Studio bude opakovaně zobrazovat výzvu k opakovanému ověření za den. Možná budete muset znovu zadat svoje přihlašovací údaje pro dřív ověřené klienty, a to i v průběhu stejné relace sady Visual Studio.

## <a name="using-visual-studio-with-mfa-policies"></a>Používání sady Visual Studio se zásadami vícefaktorového ověřování
Ve vydané verzi 16,6 jsme do sady Visual Studio 2019 přidali nové funkce, které zjednodušují přístup uživatelů k prostředkům zabezpečeným prostřednictvím zásad certifikační autority, jako je MFA. Pokud chcete použít tento rozšířený pracovní postup, musíte se přihlásit k používání výchozího webového prohlížeče vašeho systému jako mechanismu pro přidání a opětovné ověření účtů sady Visual Studio.  

> [!WARNING]
> Nepoužíváte-li tento pracovní postup, může dojít k tomu, že při přidávání nebo opětovném ověřování účtů sady Visual Studio dojde k vyvolání omezeného prostředí s výzvou k dalšímu ověřování. 

### <a name="enabling-system-web-browser"></a>Povoluje se webový prohlížeč systému.  
Chcete-li povolit tento pracovní postup, v dialogovém okně Možnosti sady Visual Studio **(nástroje > možnosti...)** vyberte kartu **účty** a v části **Přidat a znovu ověřit účty pomocí:** rozevírací seznam vyberte **systém webový prohlížeč** . 

:::image type="content" source="media/select-system-web-browser.png" alt-text="V nabídce vyberte systémový webový prohlížeč.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Přihlášení k dalším účtům se zásadami vícefaktorového ověřování 
Až bude pracovní postup webového prohlížeče zapnutý, můžete se v dialogovém okně nastavení účtu **(soubor > nastavení účtu)** přihlásit nebo přidat účty do sady Visual Studio obvyklým způsobem.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Přidejte nový účet přizpůsobení do sady Visual Studio." border="false":::

Tato akce otevře výchozí webový prohlížeč vašeho systému, požádá vás, abyste se přihlásili ke svému účtu a ověřili všechny požadované zásady vícefaktorového ověřování. 

> [!NOTE] 
> Nechte si prohlížeč otevřený prostřednictvím celého procesu, aby se zajistilo, že při zavření prohlížeče můžou aktivovat další výzvy k autorizaci. 

## <a name="reauthenticating-an-account"></a>Opětovné ověření účtu  
Pokud dojde k potížím s vaším účtem, může Visual Studio požádat o znovu zadání přihlašovacích údajů k účtu.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Znovu ověřte svůj účet sady Visual Studio.":::

Po kliknutí na znovu **zadat přihlašovací údaje** se otevře výchozí webový prohlížeč vašeho systému a pokusí se automaticky aktualizovat vaše přihlašovací údaje. Pokud to neproběhne úspěšně, budete vyzváni k přihlášení k účtu a ověření všech požadovaných zásad vícefaktorového ověřování. 

> [!NOTE] 
> Udržujte si otevřený prohlížeč prostřednictvím celého procesu, abyste mohli při zavírání prohlížeče aktivovat další výzvy k autorizaci. 

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Odhlášení od použití konkrétního tenanta Azure Active Directory v aplikaci Visual Studio

Visual Studio 2019 verze 16,6 nabízí flexibilitu pro vyfiltrování konkrétních klientů, které je skrývá ze sady Visual Studio. Filtrování eliminuje nutnost ověřování u tohoto tenanta, ale také znamená, že nebudete mít přístup k žádným přidruženým prostředkům. 

Tato funkce je užitečná v případě, že máte více tenantů, ale chcete optimalizovat vývojové prostředí tím, že zacílíte na určitou podmnožinu. Může také pomáhat v případech, kdy nemůžete ověřit konkrétní zásadu certifikační autority nebo MFA, protože je možné vyfiltrovat problematického klienta. 

### <a name="how-to-filter-out-a-tenant"></a>Jak odfiltrovat tenanta
Chcete-li filtrovat klienty přidružené k vašemu účtu aplikace Visual Studio, otevřete dialogové okno nastavení účtu **(soubor > nastavení účtu...)** a klikněte na tlačítko **použít filtr**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Použít filtr" border="false":::

Zobrazí se dialogové okno **účtu filtru** , ve kterém můžete vybrat klienty, které chcete používat s vaším účtem. 

:::image type="content" source="media/select-filter-account.png" alt-text="Vyberte účet, který chcete filtrovat.":::

## <a name="see-also"></a>Viz také

- [Přihlášení k sadě Visual Studio](signing-in-to-visual-studio.md)
- [Přihlášení k Visual Studio pro Mac](/visualstudio/mac/signing-in)
- [Práce s několika uživatelskými účty](work-with-multiple-user-accounts.md)