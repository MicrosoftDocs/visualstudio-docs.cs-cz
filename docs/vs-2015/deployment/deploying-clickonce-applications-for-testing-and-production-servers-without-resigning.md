---
title: Nasazení aplikací ClickOnce pro testovací a produkční servery bez rezignování | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395375"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Nasazování aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje novou funkci ClickOnce zavedenou v rozhraní .NET Framework verze 3.5, která umožňuje nasazení aplikací ClickOnce z více síťových umístění bez opětovného podepsání nebo změny manifestů ClickOnce.  
  
> [!NOTE]
> Rezignace je stále upřednostňovanou metodou pro nasazení nových verzí aplikací. Kdykoli je to možné, použijte metodu reřazení. Další informace naleznete v [tématu Mage.exe (Nástroj pro generování a úpravy manifestu).](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
 Vývojáři a nestátní výrobci softwaru třetích stran se mohou k této funkci přihlásit, což zákazníkům usnadní aktualizaci aplikací. Tuto funkci lze použít v následujících situacích:  
  
- Při aktualizaci aplikace není první instalace aplikace.  
  
- Pokud je v počítači pouze jedna konfigurace aplikace. Pokud je například aplikace nakonfigurována tak, aby ukazovala na dvě různé databáze, nelze tuto funkci použít.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Vyloučení zprostředkovatele nasazení z manifestů nasazení  
 V rozhraní .NET Framework 2.0 a .NET Framework 3.0 musí všechny aplikace ClickOnce, `deploymentProvider` které se nainstalují do systému pro offline dostupnost, zadat v manifestu nasazení. Často `deploymentProvider` se označuje jako umístění aktualizace; je to umístění, ve kterém ClickOnce bude kontrolovat aktualizace aplikací. Tento požadavek spolu s potřebou vydavatelů aplikací podepsat jejich nasazení, ztížilo společnosti aktualizaci aplikace ClickOnce od dodavatele nebo jiné třetí strany. Také ztěžuje nasazení stejné aplikace z více míst ve stejné síti.  
  
 Se změnami, které byly provedeny ClickOnce v rozhraní .NET Framework 3.5, je možné, aby třetí strana poskytla aplikaci ClickOnce jiné organizaci, která pak může nasadit aplikaci ve vlastní síti.  
  
 Chcete-li využít této funkce, vývojáři clickonce `deploymentProvider` aplikací musí vyloučit z jejich manifesty nasazení. To znamená `-providerUrl` vyloučení argumentu při vytváření manifestů nasazení pomocí souboru Mage.exe nebo zajištění, že textové pole **Umístění spuštění** na kartě **Manifest aplikace** zůstane prázdné, pokud generujete manifesty nasazení pomocí souboru MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider a aktualizace aplikací  
 Počínaje rozhraním .NET Framework 3.5 již není `deploymentProvider` nutné zadat v manifestu nasazení, abyste mohli nasadit aplikaci ClickOnce pro online i offline použití. To podporuje scénář, kde je třeba zabalit a podepsat nasazení sami, ale povolit jiným společnostem nasadit aplikaci přes jejich sítě.  
  
 Klíčovým bodem k zapamatování `deploymentProvider` je, že aplikace, které vylučují, nemohou během aktualizací změnit umístění instalace, dokud znovu nedodají aktualizaci, která značku obsahuje. `deploymentProvider`  
  
 Zde jsou dva příklady, které tento bod objasňují. V prvním příkladu publikujete aplikaci `deploymentProvider` ClickOnce, která nemá žádnou `http://www.adatum.com/MyApplication/`značku, a požádáte uživatele o instalaci z aplikace . Pokud se rozhodnete publikovat další aktualizaci aplikace `http://subdomain.adatum.com/MyApplication/`z aplikace , nebudete mít žádný způsob, jak `http://www.adatum.com/MyApplication/`to znamenat v manifestu nasazení, který je umístěn v aplikaci . Můžete provést jednu ze dvou věcí:  
  
- Řekněte uživatelům, aby odinstalovali předchozí verzi a nainstalovali novou verzi z nového umístění.  
  
- Zahrnout aktualizaci, která `deploymentProvider` zahrnuje `http://www.adatum.com/MyApplication/`odkazování na `http://www.adatum.com/MyApplication/` . Potom uvolněte další `deploymentProvider` aktualizaci později s odkazem na `http://subdomain.adatum.com/MyApplication/`.  
  
  V druhém příkladu publikujete aplikaci `deploymentProvider`ClickOnce, která určuje , a pak se rozhodnete ji odebrat. Jakmile bude nová `deploymentProvider` verze bez stažena klientům, nebude možné přesměrovat cestu použitou pro aktualizace, dokud `deploymentProvider` nevydáte verzi aplikace, která byla obnovena. Stejně jako v `deploymentProvider` prvním příkladu musí zpočátku ukazovat na aktuální umístění aktualizace, nikoli na nové umístění. V tomto případě, pokud se `deploymentProvider` pokusíte `http://subdomain.adatum.com/MyApplication/`vložit, který odkazuje na , pak další aktualizace se nezdaří.  
  
## <a name="creating-a-deployment"></a>Vytvoření nasazení  
 Podrobné pokyny k vytváření nasazení, která lze nasadit z různých síťových umístění, naleznete [v návodu: Ruční nasazení aplikace ClickOnce, která nevyžaduje opětovné podepsání a která zachová informace o značce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (Nástroj pro generování a úpravy manifestu)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Nástroj pro generování a úpravy manifestu, grafický klient)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
