---
title: ClickOnce a Authenticode | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9b0e22f56ab68be521eda7a765a2be7e23bbf92
ms.sourcegitcommit: 6c3aa85ff17916936018d121e7a0d1b486f6c7eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093953"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce a kód Authenticode
*Authenticode* je technologie společnosti Microsoft, která používá standardní kryptografii k podepisování kódu aplikace pomocí digitálních certifikátů, které ověřují pravost vydavatele aplikace. Použitím Authenticode pro nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace snižuje riziko trojského koně. Trojský kůň je virus nebo jiný škodlivý program, který škodlivá třetí strana zkresluje jako legitimní program pocházející ze zavedeného a důvěryhodného zdroje. Podepisování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení pomocí digitálního certifikátu je volitelný krok k ověření, že sestavení a soubory nejsou zfalšovány.

 Následující části popisují různé typy digitálních certifikátů používaných v programu Authenticode, ověřování certifikátů pomocí certifikačních úřadů (CA), roli časového razítka v certifikátech a metody ukládání, které jsou k dispozici pro Certifikáty.

## <a name="authenticode-and-code-signing"></a>Authenticode a podepisování kódu
 *Digitální certifikát* je soubor, který obsahuje kryptografickou dvojici veřejného a soukromého klíče spolu s metadaty popisujícími vydavatele, kterému byl certifikát vydán, a agenturu, která certifikát vydala.

 Existují různé typy certifikátů Authenticode. Každý z nich je nakonfigurován pro různé typy podepisování. Pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace musíte mít certifikát Authenticode, který je platný pro podepisování kódu. Pokud se pokusíte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podepsat aplikaci pomocí jiného typu certifikátu, například digitálního e-mailového certifikátu, nebude fungovat. Další informace naleznete [v tématu Úvod do podepisování kódu](/windows/desktop/seccrypto/cryptography-tools).

 Certifikát pro podepisování kódu můžete získat jedním ze tří způsobů:

- Nákup od dodavatele certifikátu

- Získejte ji od skupiny ve vaší organizaci, která je zodpovědná za vytváření digitálních certifikátů.

- Vytvořte vlastní certifikát pomocí rutiny New-SelfSignedCertificate PowerShell nebo pomocí *makecert.exe*, [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]který je součástí rutiny .

### <a name="how-using-certificate-authorities-helps-users"></a>Jak použití certifikačních autorit pomáhá uživatelům
 Certifikát generovaný pomocí nástroje New-SelfSignedCertificateCertificate nebo *MakeCert.exe* se běžně nazývá *vlastní certifikát* nebo *testovací certifikát*. Tento druh certifikátu funguje podobně jako soubor *.snk* v rozhraní .NET Framework. Skládá se výhradně z dvojice veřejných a soukromých kryptografických klíčů a neobsahuje žádné ověřitelné informace o vydavateli. Vlastní certifikáty můžete použít k [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikací s vysokou důvěryhodností v síti intranet. Pokud však tyto aplikace běží [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] v klientském počítači, budou identifikovány jako pocházející z neznámého vydavatele. Ve výchozím [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nastavení nemohou aplikace podepsané pomocí vlastních certifikátů a nasazené přes Internet využívat nasazení důvěryhodných aplikací.

 Pokud naopak obdržíte certifikát od certifikační autority, například od dodavatele certifikátu nebo oddělení v rámci rozlehlé sítě, nabízí certifikát uživatelům větší zabezpečení. Nejenže identifikuje vydavatele podepsaného softwaru, ale ověří tuto identitu kontrolou u certifikační autority, která ji podepsala. Pokud certifikační autorita není kořenovým úřadem, authenticode také "zřetězí" zpět ke kořenovému úřadu a ověří, zda je certifikační autorita oprávněna vydávat certifikáty. Chcete-li být větší zabezpečení, měli byste kdykoli použít certifikát vydaný certifikační autoritou.

 Další informace o generování vlastních certifikátů naleznete v [tématu New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) nebo [MakeCert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Časová razítka
 Platnost certifikátů používaných k podepisování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] žádostí vyprší po určité době, obvykle dvanáct měsíců. Aby bylo možné odstranit potřebu neustále znovu podepisovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pomocí nových certifikátů, podporuje časové razítko. Pokud je aplikace podepsána časovým razítkem, její certifikát bude nadále přijímán i po vypršení platnosti za předpokladu, že časové razítko je platné. To [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] umožňuje aplikacím s certifikáty, jejichž platnost vypršela, ale platnými časovými razítky, stahovat a spouštět. Umožňuje také nainstalovaným aplikacím s certifikáty, jejichž platnost vypršela, pokračovat ve stahování a instalaci aktualizací.

 Chcete-li zahrnout časové razítko na aplikační server, musí být k dispozici server časových razítek. Informace o výběru serveru časových razítek naleznete v [tématu How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Aktualizace certifikátů, jejichž platnost vypršela
 V dřívějších verzích rozhraní .NET Framework může aktualizace aplikace, jejíž platnost certifikátu vypršela, způsobit, že tato aplikace přestane fungovat. Chcete-li tento problém vyřešit, použijte jednu z následujících metod:

- Aktualizujte rozhraní .NET Framework na verzi 2.0 SP1 nebo novější v systému Windows XP nebo verze 3.5 nebo novější v systému Windows Vista.

- Odinstalujte aplikaci a znovu nainstalujte novou verzi s platným certifikátem.

### <a name="store-certificates"></a>Uložit certifikáty

- Certifikáty můžete uložit jako soubor *Pfx* do systému souborů nebo je můžete uložit uvnitř kontejneru klíčů. Uživatel v doméně systému Windows může mít několik kontejnerů klíčů. Ve výchozím nastavení bude *program MakeCert.exe* ukládat certifikáty do kontejneru osobního klíče, pokud neurčíte, že by měl být uložen do *souboru .pfx.* *Mage.exe* a *MageUI.exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nástroje pro vytváření nasazení, umožňují používat certifikáty uložené oběma způsobem.

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
