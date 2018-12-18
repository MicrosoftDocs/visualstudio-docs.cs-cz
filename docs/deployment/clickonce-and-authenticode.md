---
title: ClickOnce a kód Authenticode | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc0018533f089c2be3d0a94093bf41deadd9a74e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907440"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce a kód Authenticode
*Authenticode* je technologie společnosti Microsoft, které používá standardní kryptografie pro podepsání kódu aplikace s digitálními certifikáty, které ověření pravosti vydavatele. Pomocí technologie Authenticode pro nasazení aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] snižuje riziko trojského koně. Trojský kůň, není virus nebo jiný škodlivý program, který zkresluje skutečnost třetí strana jako legitimní program pocházejí z důvěryhodného zdroje a zavedené. Podepisování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení pomocí digitálního certifikátu je volitelný krok pro ověření, že se sestaveními a soubory nebylo manipulováno.  
  
 Následující části popisují různé druhy digitálních certifikátů používaných v Authenticode, jak certifikáty se ověřují pomocí certifikační autority (CA), role časovým razítkem v certifikátech a metody k dispozici pro úložiště certifikáty.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode a podepisování kódu  
 A *digitální certifikát* je soubor, který obsahuje veřejného a privátního klíče páru kryptografických, spolu s metadata popisující vydavatele a kterému certifikát byl vydán a subjekt, který vystavila certifikát.  
  
 Existují různé typy certifikátů Authenticode. Každý z nich je nakonfigurovaný pro různé typy podepisování. Pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací, musí mít Authenticode certifikát, který je platný pro podepisování kódu. Pokud se pokusíte přihlásit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace s jiným typem certifikátu, jako jsou e-mailu digitální certifikát, nebude fungovat. Další informace najdete v tématu [Úvod k podepisování kódu](http://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Certifikát pro podepisování v jednom ze tří způsobů kódu můžete získat:  
  
- Zakupte od dodavatele certifikátu.  
  
- Zobrazí se jedna ze skupiny ve vaší organizaci, který je zodpovědný za vytváření digitálních certifikátů.  
  
- Generovat vlastní certifikát pomocí rutiny New-SelfSignedCertificate Powershellu nebo pomocí *MakeCert.exe*, který je součástí [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Jak používat certifikační autority pomáhá uživatelům  
 Certifikát vytvořený pomocí New-SelfSignedCertificate nebo *MakeCert.exe* nástroje se běžně nazývá *samoobslužného cert* nebo *testovacího certifikátu*. Tento druh certifikátu funguje podobně stejným způsobem jako *.snk* soubor bude fungovat v rozhraní .NET Framework. Se skládá pouze z dvojice veřejného/soukromého kryptografických klíčů a neobsahuje žádné ověřitelné informace o vydavateli. Vlastní certifikáty můžete použít k nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací s vysokou důvěryhodností na intranetu. Ale pokud tyto aplikace se spouštějí na klientském počítači, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bude identifikovat jako pocházející od neznámého vydavatele. Ve výchozím nastavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace podepsána s vlastní certifikáty a nasazení přes Internet nelze využít Trusted Application Deployment.  
  
 Naopak pokud přijetí certifikátu od certifikační Autority, jako je například certifikát dodavatele nebo oddělení v rámci vašeho podniku certifikátu nabízí lepší zabezpečení pro vaše uživatele. Nejen identifikuje vydavatele softwaru podepsané, ale tuto identitu ověří tak, že zkontrolujete s certifikační Autoritou, která je podepsána. Pokud certifikační Autorita není kořenová autorita, Authenticode bude také "řetězce" zpět na kořenovou autoritou, chcete-li ověřit, že certifikační Autorita je oprávnění k vydávání certifikátů. Pro lepší zabezpečení používejte certifikát vydaný certifikační Autority, kdykoli je to možné.  
  
 Další informace o generování vlastní certifikáty najdete v tématu [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) nebo [MakeCert](/windows/desktop/SecCrypto/makecert).  
  
### <a name="timestamps"></a>Časová razítka  
 Certifikáty používané k podepisování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací vyprší po určité době obvykle dvanáct měsíců. Aby bylo možné zbavují uživatele nutnosti provádět neustále znovu podepisovat aplikace pomocí nové certifikáty [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podporuje časové razítko. Když je aplikace podepsána s časovým razítkem, svůj certifikát bude přijata i po vypršení platnosti, za předpokladu, že je platné časové razítko. Díky tomu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] s certifikáty s vypršenou platností, ale platná časová razítka ke stažení a spuštění aplikace. Umožňuje také nainstalované aplikace s certifikáty s vypršenou platností nadále stahovat a instalovat aktualizace.  
  
 Zahrnout časové razítko aplikační server, musí být k dispozici serveru časového razítka. Informace o tom, jak vybrat časového razítka serveru najdete v tématu [postupy: přihlášení aplikace a manifesty nasazení](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="update-expired-certificates"></a>Aktualizujte certifikáty s vypršenou platností  
 V dřívějších verzích rozhraní .NET Framework aktualizace prošlou platností certifikátu aplikace může způsobit, že aplikace přestane fungovat. Chcete-li tento problém vyřešit, použijte jednu z následujících metod:  
  
-   Aktualizace rozhraní .NET Framework verze 2.0 SP1 nebo později se systémem Windows XP, verze 3.5 nebo později na Windows Vista.  
  
-   Tuto aplikaci odinstalujte a znovu nainstalujte novou verzi s platným certifikátem.  
  
-   Vytvořte sestavení příkazového řádku, která aktualizuje certifikát. Podrobné informace o tomto procesu najdete v [článku technické podpory Microsoftu 925521](http://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="store-certificates"></a>Certifikáty Store  
  
- Jako certifikáty můžete uložit *.pfx* souboru v systému souborů, nebo můžete ukládat do kontejneru klíčů. Uživatel v doméně Windows může mít několik kontejnerů klíčů. Ve výchozím nastavení *MakeCert.exe* uloží certifikáty v kontejnerech osobního klíče, pokud určíte, že ho měli uložit ho. tím *.pfx* místo. *Mage.exe* a *MageUI.exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] nástroje pro vytváření [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, umožňují používat certifikáty uložené v obou způsobem.  
  
## <a name="see-also"></a>Viz také:  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)