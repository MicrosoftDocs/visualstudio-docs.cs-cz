---
title: Rozbíjení změn rozhraní API Visual Studio 2022 Preview
description: Přečtěte si o změnách rozhraní API, které způsobují selhání kompilace stávajících rozšíření VS při migraci rozšíření Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 9427b7a75ad53fc9a0795b249d96431113aba36d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308731"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Rozbíjení změn rozhraní API v Visual Studio 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Pokud migrujete rozšíření na Visual Studio 2022, můžou vás ovlivnit zde uvedené změny, které jsou narušující.

## <a name="reference-assemblies-no-longer-installed"></a>Referenční sestavení už nejsou nainstalovaná

Na řadu sestavení, na která možná odkazujete, je možné, že nástroj MSBuild Visual Studio z instalačního adresáře nástroje Visual Studio již nainstalován. NuGet byste měli použít k získání referenčních Visual Studio SDK, která potřebujete. Podrobné [kroky k tomu najdete](update-visual-studio-extension.md#modernize-your-vsix-project) v tématu Modernizace projektů.

## <a name="removed-apis"></a>Odebraná rozhraní API

V Visual Studio roce 2022 bylo v rámci přechodu na Visual Studio odebráno několik rozhraní API. Seznam odebraných rozhraní API najdete na stránce [Odebraný seznam rozhraní API.](removed-api-list.md)

## <a name="interop-breaking-changes"></a>Změny rozbíjejí interoperabilitu

Mnoho z našich rozhraní API se v Visual Studio 2022 změnilo, obvykle s jednoduchými změnami, které jsou pro váš kód jednoduché.

Pro správu rozbíjených změn plánujeme poskytnout nový mechanismus pro distribuci sestavení vzájemné spolupráce. Konkrétně pro Visual Studio 2022 a dále poskytujeme jediné sestavení vzájemné spolupráce s definicemi pro mnoho běžných veřejných Visual Studio rozhraní. Toto sestavení obsahuje spravované definice pro mnoho Visual Studio rozhraní, která se přesouvá z více sestavení vzájemné spolupráce. Nové sestavení vzájemné spolupráce se distribuuje prostřednictvím balíčku `Microsoft.VisualStudio.Interop` NuGet.

Komponenty Visual Studio, které se primárně používají v nativních kontextech a mají malý počet změn, které mají přerušení, budou mít i nadále vlastní sestavení vzájemné spolupráce (například sestavení ladicího programu bude VisualStudio.Debugger.Interop.dll stejně jako dnes). V každém případě lze na sestavení odkazovat z vaší aplikace, stejně jako je tomu dnes.

Jedná se o významnou změnu a znamená, že rozšíření, která používají rozhraní API v a sestavení sestavená v tomto novém přístupu, nejsou kompatibilní se staršími verzemi Visual Studio pomocí předchozího sestavení vzájemné spolupráce.

To má několik velmi důležitých výhod, které vám usnadní aktualizaci Visual Studio 2022:

- Jakákoli poškozená rozhraní API se stanou chybami v době sestavení, které usnadňují jejich vyhledání a opravu.
- Potřebujete jenom aktualizovat kód, který používá rozhraní API, které bylo porušené v Visual Studio 2022.
- Nebudete moct omylem použít staré, teď poškozené rozhraní API.

Celkově bude výsledkem těchto změn stabilnější verze Visual Studio pro všechny uživatele. Hlavní nevýhodou tohoto přístupu je, že spravovaná sestavení nebudou moct běžet v systémech Visual Studio 2019 i Visual Studio 2022 bez nutnosti kompilace kódu jednou pro každou cílovou Visual Studio verzi.

Při práci s chybami kompilace kvůli rozdílům rozhraní API mezi verzemi Visual Studio 2019 a Visual Studio 2022 můžete najít rozhraní API nebo vzor, které máte, uvedené níže s pokyny k jejich řešení.

### <a name="int-or-uint-where-intptr-is-expected"></a>`int` nebo `uint` kde `IntPtr` se očekává

Očekáváme, že se jedná o velmi běžnou chybu. Aby bylo Visual Studio 2022 64bitový proces, musela být některá z našich rozhraní API pro interoperabilitu opravena, kde se předpokládá, že se ukazatel vejde do 32bitového celého čísla, aby bylo možné skutečně použít hodnotu s velikostí ukazatele.

Ukázková chyba:

> Argument 3: Nelze převést z out uint na out System.IntPtr

Jednoduše aktualizujte kód tak, aby očekával, poskytl, kde nebo `IntPtr` byl použit k vyřešení `UIntPtr` `int` `uint` chyby.

Ukázková oprava:

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>Typ vzájemné spolupráce definovaný ve dvou sestaveních

Když kompilátor C# hlásí chybu, že typ, který používáte, je definovaný ve dvou sestaveních, pravděpodobně odkazujete na sestavení ze sady SDK verze Visual Studio 2019, na které byste už neměli odkazovat.

Ukázková chyba:

> chyba CS0433: V Microsoft.VisualStudio.Interop existuje typ IVsDpiAware. Version=17.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' a 'Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

Informace o tom, který název sestavení je upřednostňovaným názvem v [nástroji](migrated-assemblies.md) Visual Studio 2022, najdete v naší tabulce přemapování referenčních sestavení.
Vzhledem ke dvěma sestavením uvedeným v předchozí ukázce a zobrazení této tabulky si všimněte, že se jedná `Microsoft.VisualStudio.Interop` o nový název sestavení. Opravou by pak bylo odebrání odkazu `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` na z projektu.

V některých případech nabízíme balíček Visual Studio verze 2022 pro zastaralé sestavení, které obsahuje služby předávání typů. Pokud je tato možnost dostupná, můžete místo odebrání upgradovat odkaz na balíček Visual Studio 2022.  Přeposílání typů vyřeší chybu z kompilátoru.

Mějte na paměti, že někdy těmto odkazům může přisoudit přechodný odkaz na balíček, a proto může být obtížnější odebrat než přímý odkaz v souboru projektu. V takových případech se ujistěte, že všechny přímé odkazy na balíčky používají Visual Studio 2022 SDK. Řetězec balíčků, kteréproject.assets.jsza uvedení *zastaralého* sestavení, najdete v tématu . Aktualizace tranzitivního odkazu na balíček Visual Studio 2022 je stejně snadná jako jeho instalace jako přímý odkaz.

Pokud nemůžete změnit strom závislostí (například protože zahrnuje závislost třetí strany), můžete přidat přímý odkaz na balíček před Visual Studio 2022 a přidat k této položce metadata pro vyřešení chyby `ExcludeAssets="compile"` `PackageReference` kompilátoru. Mějte ale na paměti, že s touto technikou může vaše rozšíření zachovat závislost na sestavení před Visual Studio 2022 a vaše rozšíření může za běhu fungovat chybně.

### <a name="missing-reference-to-an-interop-assembly"></a>Chybějící odkaz na sestavení vzájemné spolupráce

Při odkazování na sestavení zkompilované proti sadě SDK před Visual Studio 2022 může dojít k chybě kvůli chybějícímu odkazu na sestavení.

Ukázková chyba:

> Chyba CS0012: Typ IVsTextViewFilter je definovaný v sestavení, na které se odkazuje. Musíte přidat odkaz na sestavení Microsoft.VisualStudio.TextManager.Interop, Version=7.1.40304.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a.

Pomocí tabulky [přemapování referenčního sestavení](migrated-assemblies.md)můžete potvrdit, že požadované sestavení ve skutečnosti není sestavení, na které byste měli odkazovat.

Nejlepší opravou je aktualizace závislosti na verzi, která byla zkompilována proti sadě Visual Studio 2022 SDK, takže kompilátor už odebrané sestavení vzájemné spolupráce nepotřebuje.

V některých případech nabízíme balíček Visual Studio verze 2022 pro zastaralé sestavení, které obsahuje služby předávání typů. Pokud je k dispozici, máte možnost přidat odkaz na balíček do zastaralého balíčku ve verzi Visual Studio 2022, aby služby předávání typů chybu z kompilátoru vyřešily.

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` chybí

Toto rozhraní obsahuje dvě definice ve dvou oborech názvů. Pouze jeden z nich byl určený ke spravované spotřebě.

Visual Studio 2019 – obor názvů | Visual Studio 2022 – obor názvů | Zamýšlené použití
--|--|--
Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Využití spravovaného kódu
Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.COMAsyncServiceProvider.IAsyncServiceProvider | Jenom interoperability nízké úrovně

Pokud se zobrazí chyba týkající se , je možné, že používáte ten, který je určený pro nativní `IAsyncServiceProvider` kód (druhý  řádek).
Pokud ano, můžete aktualizovat na nový obor názvů nebo přepnout na popisnější spravované rozhraní.

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE``_DTE`a selhání přetypování

`DTE` a `_DTE` jsou obě rozhraní. Jeden je odvozen od druhého. V Visual Studio 2022 se však základní a odvozené typy prohodí.
Díky tomu určitá přiřazení nebo přetypování typu selžou.

To také znamená, kde jste použili `new DTE()` , musíte teď použít `new _DTE()` .

### <a name="missing-argument-on-a-method-invocation"></a>Chybějící argument pro vyvolání metody

Několik metod už nedeklaruje výchozí argumenty pro volitelné parametry v rozhraní INTEROP API.
Pokud se zobrazí chyba týkající se chybějícího argumentu pro volání zprostředkovatele komunikace s objektem COM a volání parametru pro typ, může být předchozí výchozí hodnota definovaná rozhraním API zprostředkovatele komunikace `object` Visual Studio 2019 , proto zvažte přidání jako argumentu pro vyřešení chyby `""` `""` kompilace.

Pokud máte pochybnosti o tom, jaký byl výchozí argument, zkuste přepnout kontext služby jazyka z Visual Studio 2022 na Visual Studio 2019, abyste pomocí starších sestavení vzájemné spolupráce měli intellisense, abyste viděli výchozí argument, a pak ho explicitně přidejte do kódu. Po kompilaci pro Visual Studio 2019 bude i nadále fungovat, ale bude se zkompilovat pro Visual Studio 2022.

Ukázková oprava:

```diff
-process4.Attach2();
+process4.Attach2("");
```
