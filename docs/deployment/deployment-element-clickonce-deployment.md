---
title: '&lt;Element&gt; nasazení (nasazení ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 988ce0859ab24377395cc4077f9e6fa42e0487a5
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887854"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;element&gt; nasazení (nasazení ClickOnce)
Určuje atributy používané pro nasazení aktualizací a expozici systému.

## <a name="syntax"></a>Syntaxe

```xml

      <deployment
   install
   minimumRequiredVersion
   mapFileExtensions
   disallowUrlActivation
   trustUrlParameters
>
   <subscription>
         <update>
            <beforeApplicationStartup/>
            <expiration
               maximumAge
               unit
            />
         </update>
   </subscription>
   <deploymentProvider
      codebase
   />
</deployment>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 Element je povinný a je `urn:schemas-microsoft-com:asm.v2` v oboru názvů. `deployment` Element má následující atributy.

| Atribut | Popis |
|--------------------------| - |
| `install` | Povinný parametr. Určuje, zda tato aplikace definuje přítomnost v nabídce **Start** systému Windows a v Ovládacích panelech aplikace **Přidat nebo odebrat programy** . Platné hodnoty jsou `true` a `false`. Pokud `false` `subscription` , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bude vždy spouštět nejnovější verzi této aplikace ze sítě a nebude rozpoznána element. |
| `minimumRequiredVersion` | Volitelný parametr. Určuje minimální verzi této aplikace, která se dá spustit na klientovi. Pokud je číslo verze aplikace menší než číslo verze uvedené v manifestu nasazení, aplikace se nespustí. Čísla verzí musí být zadána ve formátu `N.N.N.N`, kde `N` je unsigned integer. Pokud je `install` `false`atribut ,`minimumRequiredVersion` nesmí být nastaven. |
| `mapFileExtensions` | Volitelný parametr. Výchozí hodnota je `false`. Pokud `true`všechny soubory v nasazení musí mít příponu. deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Tato rozšíření odeberou tyto soubory ihned po jejich stažení z webového serveru. Pokud publikujete aplikaci pomocí nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], toto rozšíření automaticky přidá do všech souborů. Tento parametr umožňuje stažení všech souborů v rámci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení z webového serveru, který blokuje přenos souborů končících "nebezpečné" přípony, jako je například. exe. |
| `disallowUrlActivation` | Volitelný parametr. Výchozí hodnota je `false`. Pokud `true`, zabrání spuštění nainstalované aplikace kliknutím na adresu URL nebo zadáním adresy URL do aplikace Internet Explorer. `install` Pokud atribut není přítomen, je tento atribut ignorován. |
| `trustURLParameters` | Volitelný parametr. Výchozí hodnota je `false`. Pokud `true`umožňuje, aby adresa URL obsahovala parametry řetězce dotazu, které jsou předány do aplikace, podobně jako argumenty příkazového řádku jsou předány do aplikace příkazového řádku. Další informace najdete v tématu [jak: Načte informace řetězce dotazu v online aplikaci](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)ClickOnce.<br /><br /> Pokud je `disallowUrlActivation` `true`atribut `false`, `trustUrlParameters` musí být buď vyloučen z manifestu, nebo explicitně nastaven na. |

 `deployment` Element také obsahuje následující podřízené prvky.

## <a name="subscription"></a>předplatné
 Volitelný parametr. `update` Obsahuje element. `subscription` Element nemá žádné atributy. Pokud element neexistuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , aplikace nebude nikdy vyhledávat aktualizace. `subscription` `install` Pokud `deployment` je atributelementu[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , je ignorován, protože aplikace, která je spuštěna ze sítě, vždy používá nejnovější verzi. `subscription` `false`

## <a name="update"></a>update
 Povinný parametr. Tento prvek je podřízeným `subscription` prvkem prvku a obsahuje `beforeApplicationStartup` buď `expiration` prvek, nebo. `beforeApplicationStartup`a `expiration` nemohou být současně zadány ve stejném manifestu nasazení.

 `update` Element nemá žádné atributy.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Volitelný parametr. Tento prvek je podřízeným `update` prvkem prvku a nemá žádné atributy. Když prvek existuje, aplikace se zablokuje při [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kontrole aktualizací, pokud je klient online. `beforeApplicationStartup` Pokud tento prvek neexistuje, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bude nejprve vyhledávat aktualizace na základě hodnot zadaných `expiration` pro element. `beforeApplicationStartup`a `expiration` nemohou být současně zadány ve stejném manifestu nasazení.

## <a name="expiration"></a>Vypršení platnosti
 Volitelný parametr. Tento prvek je podřízený `update` elementu a nemá žádné podřízené položky. `beforeApplicationStartup`a `expiration` nemohou být současně zadány ve stejném manifestu nasazení. Když dojde k ověření aktualizace a zjištěna aktualizovaná verze, nová verze mezipaměti se spustí, když je spuštěná stávající verze. Nová verze se pak nainstaluje při dalším spuštění [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace.

 `expiration` Element podporuje následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`maximumAge`|Povinný parametr. Určuje, jak starý má aktuální aktualizace dojít předtím, než aplikace provede kontrolu aktualizace. Časová jednotka je určena `unit` atributem.|
|`unit`|Povinný parametr. Určuje jednotku času pro `maximumAge`. Platné jednotky jsou `hours`, `days`a `weeks`.|

## <a name="deploymentprovider"></a>deploymentProvider
 Pro .NET Framework 2,0 je tento element požadován, pokud manifest nasazení obsahuje `subscription` oddíl. Pro .NET Framework 3,5 a novější je tento prvek volitelný a bude ve výchozím nastavení použita cesta k serveru a souboru, ve kterém byl nalezen manifest nasazení.

 Tento prvek je podřízeným `deployment` prvkem prvku a má následující atribut.

| Atribut | Popis |
|------------| - |
| `codebase` | Povinný parametr. Označuje umístění manifestu nasazení, který se používá k aktualizaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, jako identifikátor URI (Uniform Resource Identifier). Tento prvek také umožňuje předávat umístění aktualizací pro instalace založené na CD. Musí se jednat o platný identifikátor URI. |

## <a name="remarks"></a>Poznámky
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Aplikaci můžete nakonfigurovat tak, aby hledala aktualizace při spuštění, kontrolovala aktualizace po spuštění nebo nikdy nekontrolovala aktualizace. Chcete-li vyhledat aktualizace při spuštění, zajistěte, aby `beforeApplicationStartup` element existoval `update` v rámci elementu. Chcete-li vyhledat aktualizace po spuštění, ujistěte se `expiration` , že element existuje `update` pod prvkem a že jsou k dispozici intervaly aktualizací.

 Chcete-li zakázat kontrolu aktualizací, odeberte `subscription` prvek. Pokud zadáte v manifestu nasazení, aby nikdy nehledaly aktualizace, můžete k ruční kontrole aktualizací použít <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> metodu.

 Další informace o tom, jak se deploymentProvider vztahuje na aktualizace, najdete v tématu [volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Příklady
 Následující příklad kódu ukazuje `deployment` prvek [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] v manifestu nasazení. V příkladu se používá `deploymentProvider` element k označení upřednostňovaného umístění aktualizace.

```xml
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">
    <subscription>
      <update>
        <expiration maximumAge="6" unit="hours" />
      </update>
    </subscription>
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />
  </deployment>
```

## <a name="see-also"></a>Viz také:
- [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)