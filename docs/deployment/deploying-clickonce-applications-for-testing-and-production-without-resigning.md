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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395322"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Nasazení aplikací ClickOnce pro testování a produkční servery bez rezignování
Tento článek popisuje funkci ClickOnce zavedenou v rozhraní .NET Framework verze 3.5, která umožňuje nasazení aplikací ClickOnce z více síťových umístění bez opětovného podepsání nebo změny manifestů ClickOnce.

> [!NOTE]
> Rezignace je stále upřednostňovanou metodou pro nasazení nových verzí aplikací. Kdykoli je to možné, použijte metodu reřazení. Další informace naleznete v [ *tématu Mage.exe* (Nástroj pro generování a úpravy manifestu).](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)

 Vývojáři a nestátní výrobci softwaru třetích stran se mohou k této funkci přihlásit, což zákazníkům usnadňuje aktualizaci aplikací. Tuto funkci lze použít v následujících situacích:

- Při aktualizaci aplikace, nikoli pro první instalaci aplikace.

- Pokud je v počítači pouze jedna konfigurace aplikace. Pokud je například aplikace nakonfigurována tak, aby ukazovala na dvě různé databáze, nelze tuto funkci použít.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Vyloučit zprostředkovatele nasazení z manifestů nasazení
 V rozhraní .NET Framework 2.0 a .NET Framework 3.0 musí všechny aplikace ClickOnce, `deploymentProvider` které se nainstalují do systému pro dostupnost offline, uvést a v manifestu nasazení. Často `deploymentProvider` se označuje jako umístění aktualizace; je umístění, kde ClickOnce kontroluje aktualizace aplikace. Tento požadavek spolu s potřebou vydavatelů aplikací podepsat jejich nasazení, ztížilo společnosti aktualizaci aplikace ClickOnce od dodavatele nebo jiné třetí strany. Také ztěžuje nasazení stejné aplikace z více míst ve stejné síti.

 Se změnami, které byly provedeny ClickOnce v rozhraní .NET Framework 3.5, je možné, aby třetí strana poskytla aplikaci ClickOnce jiné organizaci, která pak může nasadit aplikaci ve vlastní síti.

 Chcete-li využít této funkce, vývojáři clickonce `deploymentProvider` aplikací musí vyloučit z jejich manifesty nasazení. Tento požadavek znamená, `-providerUrl` že je nutné vyloučit argument při vytváření manifestů nasazení s Mage.exe. Nebo pokud generujete manifesty nasazení s MageUI.exe, musíte se ujistit, že textové pole **Umístění spuštění** na kartě **Manifest aplikace** zůstane prázdné.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider a aktualizace aplikací
 Počínaje rozhraním .NET Framework 3.5 již není `deploymentProvider` nutné zadat v manifestu nasazení, abyste mohli nasadit aplikaci ClickOnce pro online i offline použití. Tato změna podporuje scénář, kde je třeba zabalit a podepsat nasazení sami, ale umožnit jiným společnostem nasadit aplikaci přes jejich sítě.

 Důležité je mít na paměti, `deploymentProvider` že aplikace, které vylučují, nemohou `deploymentProvider` během aktualizací změnit umístění instalace, dokud znovu nedodají aktualizaci, která značku obsahuje.

 Zde jsou dva příklady, které tento bod objasňují. V prvním příkladu publikujete aplikaci `deploymentProvider` ClickOnce, která nemá žádnou `http://www.adatum.com/MyApplication/`značku, a požádáte uživatele o instalaci z aplikace . Pokud se rozhodnete publikovat další aktualizaci aplikace `http://subdomain.adatum.com/MyApplication/`z aplikace , nemáte žádný způsob, jak to `http://www.adatum.com/MyApplication/`znamenat v manifestu nasazení, který je umístěn v aplikaci . Můžete provést jednu ze dvou věcí:

- Řekněte uživatelům, aby odinstalovali předchozí verzi a nainstalovali novou verzi z nového umístění.

- Zahrnout aktualizaci, která `deploymentProvider` zahrnuje `http://www.adatum.com/MyApplication/`odkazování na `http://www.adatum.com/MyApplication/` . Potom uvolněte další `deploymentProvider` aktualizaci později s odkazem na `http://subdomain.adatum.com/MyApplication/`.

  V druhém příkladu publikujete aplikaci `deploymentProvider`ClickOnce, která určuje , a pak se rozhodnete ji odebrat. Jakmile je nová `deploymentProvider` verze bez stažena klientům, nelze přesměrovat cestu použitou pro aktualizace, dokud neuvolníte verzi aplikace, která byla obnovena. `deploymentProvider` Stejně jako v `deploymentProvider` prvním příkladu musí zpočátku ukazovat na aktuální umístění aktualizace, nikoli na nové umístění. V tomto případě pokud se `deploymentProvider` pokusíte vložit, který odkazuje na `http://subdomain.adatum.com/MyApplication/`, pak další aktualizace se nezdaří.

## <a name="create-a-deployment"></a>Vytvoření nasazení
 Podrobné pokyny k vytváření nasazení, která lze nasadit z různých síťových umístění, naleznete [v návodu: Ruční nasazení aplikace ClickOnce, která nevyžaduje opětovné podepsání a která zachová informace o značce](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Viz také
- [*Mage.exe* (Nástroj pro generování a úpravy manifestu)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Nástroj pro generování a úpravy manifestu, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
