---
title: Použití účtů, které vyžadují vícefaktorové ověřování
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Naučte se používat Visual Studio s účty, které vyžadují vícefaktorové ověřování.
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9ac42ccff8c7bffcc22c453002aad1caf6935d28
ms.sourcegitcommit: e4630a3bb89b4d606fe2cbd709bc773c5b538b78
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2021
ms.locfileid: "112975674"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Jak používat Visual Studio s účty, které vyžadují vícefaktorové ověřování

Při spolupráci s externími uživateli guest je vhodné chránit vaše aplikace a data pomocí zásad podmíněného **přístupu,** jako je vícefaktorové ověřování **(MFA).**  

Po povolení budou uživatelé hosta potřebovat více než jen uživatelské jméno a heslo pro přístup k vašim prostředkům a musí splňovat další požadavky na zabezpečení. Zásady vícefaktorového ověřování je možné vynucovat na úrovni tenanta, aplikace nebo jednotlivých uživatelů typu host úplně stejným způsobem, jako když se používají u členů vaší organizace. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>Jak jsou Visual Studio prostředí ovlivněné zásadami MFA?
Verze Visual Studio starší než 16.6 mohou mít možnosti degradování ověřování při použití s účty, které mají povolené zásady certifikační autority, jako je MFA, a jsou přidružené ke dvěma nebo více tenantům.

Tyto problémy mohou způsobit, že vaše instance Visual Studio několikrát denně znovu vyzvat k opakovaného ověření. Je možné, že budete muset znovu zadat přihlašovací údaje pro dříve ověřené tenanty, a to i v průběhu Visual Studio relace.

## <a name="using-visual-studio-with-mfa-policies"></a>Použití Visual Studio se zásadami MFA
Ve verzi 16.6 jsme do Visual Studio 2019 přidali nové možnosti, které zjednodušují přístup uživatelů k prostředkům zabezpečeným prostřednictvím zásad certifikační autority, jako je MFA. Pokud chcete tento vylepšený pracovní postup použít, budete se muset přihlásit k používání výchozího webového prohlížeče systému jako mechanismu pro přidání a opětovné ověření Visual Studio účtů.  

> [!WARNING]
> Pokud tento pracovní postup nepoužít, může to aktivovat degradované prostředí, které vede k několika dalším výzvám k ověření při přidávání nebo opětovném ověřování Visual Studio účtů. 

### <a name="enabling-system-web-browser"></a>Povolení systémového webového prohlížeče

> [!NOTE] 
> Pro co nejlepší prostředí doporučujeme před pokračováním v tomto pracovním postupu vymazat výchozí data webového prohlížeče vašeho systému. Kromě toho, pokud máte pracovní nebo školní účty v nastavení Windows 10 v části Přístup do práce nebo do školy **,** ověřte, že jsou správně ověřené.

Pokud chcete tento pracovní postup povolit, přejděte do dialogového okna Možnosti Visual Studio **(Nástroje > Možnosti...),** vyberte kartu Účty a v rozevíracím seznamu Přidat a znovu ověřovat účty **pomocí:** vyberte Systémový webový prohlížeč.   

:::image type="content" source="media/select-system-web-browser.png" alt-text="V nabídce vyberte systémový webový prohlížeč.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Přihlášení k dalším účtům pomocí zásad MFA 
Po povolení pracovního postupu systémového webového prohlížeče se můžete přihlásit nebo přidat účty do služby Visual Studio běžným způsobem prostřednictvím dialogového okna Nastavení účtu **(Soubor > Nastavení účtu...).**   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Přidejte nový účet přizpůsobení do Visual Studio." border="false":::

Tato akce otevře výchozí webový prohlížeč vašeho systému, požádá vás o přihlášení ke svému účtu a ověření všech požadovaných zásad MFA.

Během procesu přihlašování se může zobrazit další výzva s výzvou, abyste zůstali přihlášeni. Tato výzva se pravděpodobně zobrazí při druhém přihlášení účtu. Pokud chcete minimalizovat potřebu znovu zadávat přihlašovací údaje, doporučujeme vybrat **Ano,** protože tím zajistíte, že se vaše přihlašovací údaje zachovají napříč relacemi prohlížeče.

:::image type="content" source="media/kmsi.png" alt-text="Zůstat přihlášeni?":::

Na základě vašich vývojových aktivit a konfigurace prostředků se může během relace zobrazit výzva k opětovnému zadání přihlašovacích údajů. K tomu může dojít při přidání nového prostředku nebo pokusu o přístup k prostředku bez předchozího splnění požadavků na autorizaci certifikační autority nebo MFA.

## <a name="reauthenticating-an-account"></a>Opětovné ověření účtu  
Pokud dojde k problému s vaším účtem, Visual Studio požádat o opětovné zadání přihlašovacích údajů k účtu.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Znovu Visual Studio účet.":::

Kliknutím na **Znovu zadat přihlašovací údaje** otevřete výchozí webový prohlížeč vašeho systému a pokuste se přihlašovací údaje automaticky aktualizovat. V případě neúspěchu budete požádáni o přihlášení ke svému účtu a ověření všech požadovaných zásad ca/MFA.

> [!NOTE] 
> Pokud chcete mít nejlepší prostředí, nechte prohlížeč otevřený, dokud se pro vaše prostředky neověřují všechny zásady CA/MFA. Zavřením prohlížeče může dojít ke ztrátě dříve vytvořeného stavu MFA a může se zobrazit výzva k další autorizaci.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Jak vyjádřit výslovný nesouhlas s používáním konkrétního tenanta Azure Active Directory v Visual Studio

Visual Studio 2019 verze 16.6 nabízí flexibilitu odfiltrovat tenanty jednotlivě nebo globálně a efektivně je schovávat od Visual Studio. Filtrování eliminuje potřebu ověřování u tohoto tenanta, ale také to znamená, že nebudete mít přístup k žádným přidruženým prostředkům.

Tato funkce je užitečná, když máte více tenantů, ale chcete optimalizovat vývojové prostředí cílením na konkrétní podmnožinu. Může vám to také pomoct v případech, kdy nemůžete ověřit konkrétní zásady CA/MFA, protože můžete odfiltrovat urážejícího tenanta. 

### <a name="how-to-filter-out-all-tenants"></a>Jak odfiltrovat všechny tenanty
Pokud chcete globálně odfiltrovat všechny tenanty, otevřete dialogové okno Nastavení účtu (Nastavení účtu **>...)** a zrušte zaškrtnutí políčka Ověřit ve všech **adresářích Azure Active** Directory.

Zrušením výběru této možnosti zajistíte, že se budete ověřovat jenom u výchozího tenanta účtu. Také to znamená, že nebudete mít přístup k žádným prostředkům přidruženým k jiným tenantům, na které váš účet může být host.

### <a name="how-to-filter-out-individual-tenants"></a>Jak odfiltrovat jednotlivé tenanty
Pokud chcete filtrovat tenanty přidružené k vašemu Visual Studio, otevřete dialogové okno Nastavení účtu (Nastavení účtu **>...)** a klikněte na **Použít filtr**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Použijte filtr." border="false":::

Zobrazí **se dialogové** okno Filtrovat účet, ve kterém můžete vybrat tenanty, které chcete se svým účtem používat. 

:::image type="content" source="media/select-filter-account.png" alt-text="Vyberte účet, který chcete filtrovat.":::

## <a name="see-also"></a>Viz také

- [Přihlášení k sadě Visual Studio](signing-in-to-visual-studio.md)
- [Přihlaste se k Visual Studio pro Mac](/visualstudio/mac/signing-in)
- [Práce s několika uživatelskými účty](work-with-multiple-user-accounts.md)
