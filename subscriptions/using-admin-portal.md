---
title: Použití portálu správce | Visual Studio Marketplace
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Další informace o správě předplatných sady Visual Studio vaší organizace pomocí portálu pro správce.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 63f3cbc3b4eb108a17c85eaa46992989a6dac742
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42623905"
---
#  <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>Pomocí portálu pro správce předplatných sady Visual Studio

Mějte na paměti při použití Visual Studio předplatná portálu pro správu:
 
- **Předplatná sady Visual Studio mají licenci na uživatele.** Každý předplatitel na tolik počítačů, jak je potřebné pro vývoj a testování používat software. 
- **Přiřaďte úroveň jenom jedno předplatné pro každý předplatitel**, odpovídající předplatné sady Visual Studio, vaše organizace koupila. Pokud máte předplatitelé s přiřazenou víc než jednu úroveň předplatného, upravte jejich nastavení tak, aby uživatel pouze nějakou. 
- **Úroveň předplatného předplatitele bude potřeba aktualizovat** Pokud je předplatné upgradovat (po zakoupení "stupňované" licenci) nebo obnovit na nižší úrovni. 
- **Nesdílejte předplatná mezi předplatitele.** Předplatné je nutné přiřadit každému, kdo používá nebo její část výhody předplatného (software pro vývoj a testování, Microsoft Azure, e-learning, atd.). 

## <a name="administrator-roles"></a>Role správce

Existují dva různé role, které existují v nový portál správy předplatných Visual Studio pro zákazníky s multilicenčními programy. Pracovníci v těchto rolích v tuto chvíli jako primární nebo informační kontakt role a role správce předplatných ve VLSC. 

**Super admins:** při prvním nastavování organizace se stane primární nebo informační kontakt supersprávce ve výchozím nastavení. Primární nebo informační kontakt můžete přiřadit další supersprávců, kteří jsou nebo správci. Supersprávce můžete přidávat a odebírat další správce, jakož i předplatitele. Pokud existuje více než dva supersprávců, kteří jsou v systému, – supersprávce odstranit všechny kromě poslední dva pro zabezpečení. 

**Správci:** správce může nastavit pouze pomocí super správce. Správce může spravovat předplatitele v smlouvy, které přiřadí super admin k nim. 

## <a name="getting-started"></a>Začínáme

Abyste mohli spravovat předplatná vaší organizace pomocí portálu správce, musíte nejprve připojit vaše organizace k portálu.  Po dokončení registrace, je vhodné se seznámit s účastníky a podrobnosti stránky, jak jsou, kde najdete nástroje a informace, které potřebujete k provádění úloh správy vašeho předplatného.  

### <a name="onboarding"></a>Registrace

Pokud vaše organizace je připravené k odeslání zařazeni na portál pro správu předplatných Visual Studio se odešle e-mail primární a informační kontakt vyzývající k dokončení procesu registrace. Podrobnosti uvedené níže jsou uvedené kroky, které bude třeba provést pro připojení k novému portálu. Pokud byste o ni návod k technikám, najdete v tomto [správce registrace videa](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting) nebo to [článek podpory](https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "Visual Studio předplatná správce procesu migrace").   
1.  **Vyhledáním čísla PCN a přihlášení:**
    - V e-mailu primární a informační kontakt jsou součástí jedinečného odkazu a poslední tři číslice z jejich veřejné zákaznické číslo (PCN). * 
    - K získání celého čísla PCN, třeba adresu primárního kontaktu pro přihlášení k webu VLSC (pokyny k vyhledání PCN najdete existuje). 
    - Po získání PCN, budete potřebovat k výběru jejich jedinečného odkazu, která je vyzve k přihlášení. Budou moct přihlásit pomocí pracovní nebo školní účet (Pokud je vaše organizace v AAD) nebo účet Microsoft (MSA), pokud vaše organizace není v AAD. 
    - V dalším kroku se potřebují zadáte PCN. 
2.  **Nastavení správce.** Jakmile zadáte PCN, že se zaregistruje jako supersprávce v novém systému a budete moct přidat další supersprávci a správci (dříve označovaní jako manažeři předplatného). Abyste neztratili přístup by se měly dokončit ještě před datem migrace vaší organizace. 
3.  **Přístup k novému portálu pro správu předplatného.**  Jakmile se vaše organizace migrována, se odešlou e-maily na nově přidaných supersprávci a správci vyzývající k přístupu na novém portálu a zahájení správy předplatných.  

> [!NOTE]
> Pokud primární nebo informační kontakt zobrazí více než jednu e-mailu, to znamená, že mají více než jedno číslo PCN. Bude potřeba provést použitím jedinečného odkazu pro číslo PCN odkazovat v každé email.*

Pokud je potřeba přidat na nový portál pro správu předplatných Visual Studio a nejste si jisti, který je váš primární nebo informační kontakt, najdete tyto informace po přihlášení k [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx). Podívejte se na [najít váš primární kontakt](find-primary-contact.md) tématu najdete postup vyhledejte svůj primární nebo informační kontakt ve VLSC.
Pokud již byl nastavíte jako správce a potom můžete přejít přímo na [portál pro správu předplatných sady Visual Studio](https://manage.visualstudio.com).

### <a name="understanding-the-subscribers-page"></a>Vysvětlení stránky předplatitele
Po přiřazení předplatného můžete na kartě předplatitele poskytuje podrobné informace o vaši předplatitelé, včetně:
- První a poslední název každý předplatitel.
- E-mailovou adresu pro tohoto uživatele.
- Úroveň předplatného, které jim byly přiřazeny.
- Data, která byla přiřazena svoje předplatné. 
- Datum vypršení platnosti jeho předplatného.
- Volitelné textový popis.
- Údaj o tom, jestli ke stažení pro předplatitele byl povolen nebo zakázán. 
- Země, ve které se nacházejí.
- Jejich preferovaný jazyk pro e-mail s přiřazením komunikaci z portálu pro správu.
- Volitelné pole pro jinou e-mailovou adresu použitou pro komunikaci než přihlášení. 

Na levé straně této stránky lze zobrazit další informace o počtu licencí předplatné zakoupené, přiřazené a stále k dispozici ve vaší organizaci pro každou smlouvu.
> [!div class="mx-imgBorder"]
> ![Stránku předplatitele portál pro správu předplatných sady Visual Studio](_img/using-admin-portal/subscribers-page.png)

### <a name="understanding-the-details-page"></a>Stránce s podrobnostmi o vysvětlení
Další informace o smlouvě, že si prohlížíte vyberte na kartě s podrobnostmi. Zobrazuje stav smlouvy, nákupní účet, organizační údaje, primární kontakty (VLSC), supersprávci (Pokud je k dispozici) a další relevantní informace.
> [!div class="mx-imgBorder"]
> ![Stránka podrobností portál pro správu předplatných sady Visual Studio](_img/using-admin-portal/details-page.png)

