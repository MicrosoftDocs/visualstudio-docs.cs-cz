---
title: Nasazování aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abfa170fe0f30cbc4fac941a6d77d0ac8b407f7f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846587"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Nasazení aplikací ClickOnce pro testování a produkční servery bez opětovného podpisu
Tento článek popisuje funkce zavedené v rozhraní .NET Framework verze 3.5, která umožňuje nasazení aplikací ClickOnce z více umístění v síti bez opětovné podepsání nebo změna ClickOnce, manifesty ClickOnce.  
  
> [!NOTE]
>  Opětovné podepisování je stále upřednostňovanou metodou pro nasazení nové verze aplikací. Kdykoli je to možné, použijte metodu opětovného podepisování. Další informace najdete v tématu [ *Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Vývojáři třetích stran a nezávislé výrobce softwaru můžete vyjádřit výslovný souhlas k této funkci snadnější svým zákazníkům aktualizovat svoje aplikace. Tuto funkci můžete použít v následujících situacích:  
  
-   Při aktualizaci aplikace, není při první instalaci aplikace.  
  
-   Pokud existuje pouze jedna konfigurace aplikace na počítači. Například pokud aplikace je nakonfigurovaná tak, aby odkazoval na dvou různých databázích, nemůžete použít tuto funkci.  
  
## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Vyloučení deploymentProvider manifesty nasazení  
 V rozhraní .NET Framework 2.0 a rozhraní .NET Framework 3.0, musí každá aplikace ClickOnce, která nainstaluje systém, hledá offline dostupnosti seznamu `deploymentProvider` v manifestu nasazení. `deploymentProvider` Se často označuje jako umístění aktualizace; je umístění, kde ClickOnce vyhledá aktualizace aplikace. Tento požadavek, spolu s potřebu vydavatelé aplikací k podepisování svých nasazení bylo obtížné zjišťovat společnosti k aktualizaci aplikace ClickOnce od dodavatele nebo jiné aplikace třetí strany. Také umožňuje složitější nasazení stejnou aplikaci z více míst ve stejné síti.  
  
 Změny, které byly provedeny ClickOnce v rozhraní .NET Framework 3.5 je možné třetí straně poskytnout aplikace ClickOnce do jiné organizace, které pak můžete nasadit aplikaci na vlastní síť.  
  
 Aby bylo možné tuto funkci využít, musí vývojáři aplikací ClickOnce vyloučit `deploymentProvider` z jejich nasazení manifestů. Tento požadavek znamená, že je nutné vyloučit `-providerUrl` manifesty argument, když vytvoříte nasazení s Mage.exe. Nebo, pokud jsou generování manifesty nasazení s MageUI.exe, je třeba Ujistěte se, že **umístění spuštění** textového pole na **Manifest aplikace** karta je ponecháno prázdné.  
  
## <a name="deploymentprovider-and-application-updates"></a>aktualizace deploymentProvider a aplikace  
 Od verze rozhraní .NET Framework 3.5, nepotřebujete k určení `deploymentProvider` v manifestu nasazení k nasazení aplikace ClickOnce pro použití online i offline. Tato změna podporuje scénář, kde je potřeba balíček a podepsat nasazení, ale povolit jinými společnostmi dohody o nasazení aplikace v jejich sítích.  
  
 Je důležité si pamatovat, že aplikace, které vyloučit `deploymentProvider` nelze změnit jejich umístění instalace během aktualizace, dokud nebude dodána aktualizace, která zahrnuje `deploymentProvider` označit znovu.  
  
 Tady jsou dva příklady pro objasnění tohoto bodu. V prvním příkladu, publikování aplikace ClickOnce, která nemá žádné `deploymentProvider` značku a zeptejte se uživatele k jeho nainstalování z http://www.adatum.com/MyApplication/. Pokud je rozhodnout, kterou chcete publikovat další aktualizace aplikací z http://subdomain.adatum.com/MyApplication/, nemůžete nijak to zaznamenat v manifestu nasazení, který se nachází v http://www.adatum.com/MyApplication/. Jedním ze dvou kroků:  
  
- Řekněte uživatelům, aby odinstalovat předchozí verzi a nainstalujte novou verzi z nového umístění.  
  
- Zahrnout aktualizace na http://www.adatum.com/MyApplication/ , který obsahuje `deploymentProvider` odkazující na http://www.adatum.com/MyApplication/. Uvolněte později s jinou aktualizaci `deploymentProvider` odkazující na http://subdomain.adatum.com/MyApplication/.  
  
  V druhém příkladu publikování aplikace ClickOnce, která určuje `deploymentProvider`, a potom se rozhodnete ho odebrat. Jednou na novou verzi bez `deploymentProvider` se stáhne do klientů, nelze přesměrovat cestu používané pro aktualizace, dokud vydání verze aplikace, která má `deploymentProvider` obnovit. Stejně jako v prvním příkladu `deploymentProvider` zpočátku musí odkazovat na aktuální umístění aktualizace, nikoliv do nového umístění. V takovém případě pokud se pokusíte vložit `deploymentProvider` , který odkazuje na http://subdomain.adatum.com/MyApplication/, příští aktualizace selže.  
  
## <a name="create-a-deployment"></a>Vytvoření nasazení  
 Podrobné pokyny k vytvoření nasazení, která se dají nasadit z různých síťových umístěních, najdete v části [návod: Ruční nasazení aplikace ClickOnce, která nevyžaduje opětovné podepsání a které zachovává údaje o poskytovateli](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
## <a name="see-also"></a>Viz také:  
 [*Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [*MageUI.exe* (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)