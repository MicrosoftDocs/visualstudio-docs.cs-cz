---
title: Nasazení aplikací ClickOnce bez opětovného podepisování
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395322"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Nasazení aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání
Tento článek popisuje funkci ClickOnce představenou ve verzi .NET Framework 3,5, která umožňuje nasazení aplikací ClickOnce z více síťových umístění bez opětovného podepsání nebo změny manifestů ClickOnce.

> [!NOTE]
> Opětovné podepisování je stále upřednostňovanou metodou pro nasazení nových verzí aplikací. Kdykoli je to možné, použijte metodu opětovného podepsání. Další informace najdete v tématu [ *Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Vývojáři třetích stran a prodejci softwaru můžou k této funkci přihlášeni, což usnadňuje zákazníkům aktualizovat jejich aplikace. Tato funkce se dá použít v následujících situacích:

- Při aktualizaci aplikace, ne pro první instalaci aplikace.

- V případě, že je v počítači pouze jedna konfigurace aplikace. Pokud je například aplikace nakonfigurovaná tak, aby odkazovala na dvě různé databáze, nemůžete tuto funkci použít.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Vyloučit deploymentProvider z manifestů nasazení
 V .NET Framework 2,0 a .NET Framework 3,0 musí každá aplikace ClickOnce, která je nainstalována v systému pro offline dostupnost, mít `deploymentProvider` v manifestu nasazení seznam a. `deploymentProvider`Je často označován jako umístění aktualizace. Jedná se o umístění, kde aplikace ClickOnce kontroluje aktualizace aplikací. Tento požadavek spolu s nutností, aby vydavatelé aplikací podepsali svá nasazení, což společnosti bylo obtížné aktualizovat aplikaci ClickOnce od dodavatele nebo jiné třetí strany. Je také obtížné nasadit stejnou aplikaci z více míst ve stejné síti.

 Se změnami, které byly provedeny v rámci ClickOnce v .NET Framework 3,5, může třetí strana poskytnout aplikaci ClickOnce jiné organizaci, která pak může nasadit aplikaci do vlastní sítě.

 Aby bylo možné tuto funkci využít, vývojáři aplikací ClickOnce musí `deploymentProvider` ze svých manifestů nasazení vyloučit. Tento požadavek znamená, že při `-providerUrl` vytváření manifestů nasazení pomocí Mage.exe musíte vyloučit tento argument. Nebo pokud generujete manifesty nasazení pomocí MageUI.exe, musíte se ujistit, že textové pole **umístění spuštění** na kartě **manifest aplikace** zůstane prázdné.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider a aktualizace aplikace
 Počínaje verzí .NET Framework 3,5 již nemusíte v manifestu nasazení určovat, aby bylo `deploymentProvider` možné nasadit aplikaci ClickOnce pro použití v režimu online i offline. Tato změna podporuje scénář, ve kterém potřebujete zabalit a podepsat nasazení sami, ale umožněte jiným společnostem nasadit aplikaci přes jejich sítě.

 Je důležité si uvědomit, že aplikace, které vylučují, `deploymentProvider` nemohou měnit umístění instalace během aktualizací, dokud dostanou aktualizaci, která obsahuje `deploymentProvider` značku znovu.

 Tady jsou dva příklady pro objasnění tohoto bodu. V prvním příkladu publikujete aplikaci ClickOnce, která nemá žádnou `deploymentProvider` značku, a požádáte uživatele, aby si ji instalovali `http://www.adatum.com/MyApplication/` . Pokud se rozhodnete, že chcete publikovat další aktualizaci aplikace z nástroje `http://subdomain.adatum.com/MyApplication/` , neexistuje žádný způsob, jak to označit v manifestu nasazení, který se nachází v `http://www.adatum.com/MyApplication/` . Můžete provést jednu z následujících akcí:

- Informujte uživatele o odinstalaci předchozí verze a nainstalujte novou verzi z nového umístění.

- Zahrňte aktualizaci na `http://www.adatum.com/MyApplication/` , která obsahuje `deploymentProvider` ukazující na `http://www.adatum.com/MyApplication/` . Pak další aktualizaci uvolněte později pomocí `deploymentProvider` kurzoru na `http://subdomain.adatum.com/MyApplication/` .

  V druhém příkladu publikujete aplikaci ClickOnce, která určuje `deploymentProvider` a následně se rozhodnete ji odebrat. Jakmile je nová verze bez `deploymentProvider` stažení do klientů, nelze přesměrovat cestu použitou pro aktualizace, dokud nevyberete verzi aplikace, která byla `deploymentProvider` obnovena. Stejně jako u prvního příkladu `deploymentProvider` musí zpočátku nasměrovat na aktuální umístění aktualizace, nikoli na nové umístění. V takovém případě, pokud se pokusíte vložit `deploymentProvider` , který odkazuje na `http://subdomain.adatum.com/MyApplication/` , pak se další aktualizace nezdaří.

## <a name="create-a-deployment"></a>Vytvoření nasazení
 Podrobné pokyny týkající se vytváření nasazení, která se dají nasadit z různých síťových umístění, najdete v tématu [Návod: Ruční nasazení aplikace ClickOnce, která nevyžaduje Opětovné podepsání a které zachovává informace o značkách](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Viz také
- [*Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
