---
title: Použití účtů, které vyžadují vícefaktorové ověřování
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Naučte se používat Visual Studio s účty, které vyžadují službu Multi-Factor Authentication.
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 6b85d64d3f84bce34f2a9b30d9caf01127149abc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878484"
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

> [!NOTE] 
> Pro dosažení co nejlepších výsledků doporučujeme, abyste před pokračováním v tomto pracovním postupu vymazali výchozí data webového prohlížeče v systému. Pokud navíc máte pracovní nebo školní účty v nastavení Windows 10 v části přístup do **práce nebo do školy**, ověřte prosím, jestli jsou správně ověřené.

Chcete-li povolit tento pracovní postup, v dialogovém okně Možnosti sady Visual Studio **(nástroje > možnosti...)** vyberte kartu **účty** a v části **Přidat a znovu ověřit účty pomocí:** rozevírací seznam vyberte **systém webový prohlížeč** . 

:::image type="content" source="media/select-system-web-browser.png" alt-text="V nabídce vyberte systémový webový prohlížeč.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Přihlášení k dalším účtům se zásadami vícefaktorového ověřování 
Až bude pracovní postup webového prohlížeče zapnutý, můžete se v dialogovém okně nastavení účtu **(soubor > nastavení účtu)** přihlásit nebo přidat účty do sady Visual Studio obvyklým způsobem.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Přidejte nový účet přizpůsobení do sady Visual Studio." border="false":::

Tato akce otevře výchozí webový prohlížeč vašeho systému, požádá vás, abyste se přihlásili ke svému účtu a ověřili všechny požadované zásady vícefaktorového ověřování.

Během procesu přihlašování se může zobrazit další výzva s výzvou, abyste si mohli zůstat přihlášeni. Tato výzva se nejspíš zobrazí při druhém použití účtu k přihlášení. Chcete-li minimalizovat nutnost opětovného zadání přihlašovacích údajů, doporučujeme vybrat možnost **Ano**, protože tím zajistíte, aby se vaše přihlašovací údaje zachovaly napříč relacemi prohlížeče.

:::image type="content" source="media/kmsi.png" alt-text="Máte zůstat přihlášeni?":::

V závislosti na vašich vývojářských aktivitách a konfiguraci prostředků se může při vaší relaci stále zobrazovat výzva k zadání přihlašovacích údajů. K tomu může dojít, když přidáte nový prostředek, nebo se pokusíte získat přístup k prostředku, aniž jste předtím splnili požadavky na autorizaci CA nebo MFA.

## <a name="reauthenticating-an-account"></a>Opětovné ověření účtu  
Pokud dojde k potížím s vaším účtem, může Visual Studio požádat o znovu zadání přihlašovacích údajů k účtu.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Znovu ověřte svůj účet sady Visual Studio.":::

Po kliknutí na znovu **zadat přihlašovací údaje** se otevře výchozí webový prohlížeč vašeho systému a pokusí se automaticky aktualizovat vaše přihlašovací údaje. Pokud to neproběhne úspěšně, zobrazí se výzva, abyste se přihlásili ke svému účtu a ověřili všechny požadované zásady CA/MFA.

> [!NOTE] 
> Pro dosažení co nejlepších výsledků Udržujte prohlížeč otevřený, dokud nebudou pro vaše prostředky ověřeny všechny zásady certifikační autority nebo ověřování. Zavření prohlížeče může mít za následek ztrátu dříve vytvořeného stavu MFA a může vyžadovat další výzvy k autorizaci.

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
