# ExtremDumper kimdir ?? 🚀
İnfinityWare yazılım grubunun cs-go offsetleri depoladığı yerdir . bedava yazılımınızın offsetleri ve diğer yazılım grubunun offsetlerini kolayca bulabilmesi için hazırlanmıştır 
Gaye amacımız bu sektördeki herkese yardım edebilmektir.

## Yerel Oyuncu:

Geçmişte Yerel Oyuncu imzası birkaç kez kırıldığından ve / veya yanlış bir şeye işaret ettiğinden, size bir alternatif sunmak istiyorum.
Gerekli tüm ofsetler zaten repoda, insanların% 99'unu neden kullanmadığı tartışmalı - ya da çok yetersiz ve şikayet ediyorlar
hiçbir şey işe yaramaz, ancak tek bir imza bulamazlar. Ancak, hemen hemen her bilgisayar korsanlığı varlık listesini kullanır
(`dwEntityList`)
ve ayrıca ClientState (`dwClientState`). İhtiyacınız olan tek şey ClientState'de bulunan ve dwClientState_GetLocalPlayer adı verilen üçüncü bir ofset.

```C++
const auto client_state = read_memory<std::uint32_t>( engine_image->base + hazedumper::signatures::dwClientState );
if( client_state ) {
    const auto local_player = get_client_entity( 
        read_memory<std::int32_t>( client_state + hazedumper::signatures::dwClientState_GetLocalPlayer )
    );

    if( local_player ) {
        printf(
            "[+] Found local player: 0x%X, health: %d\n",
            local_player,
            read_memory<std::int32_t>( local_player + hazedumper::netvars::m_iHealth )
        );
    }
}
```

## Bilgiler:

- Biz grup olarak çoğumuz okudumuz için yada çalıştımız için, bir güncelleme olup olmadığını 7/24 göremiyoruz ve sonra itiyoruz. Bunun mümkün olan en kısa sürede gerçekleşmesini sağlamak için her türlü çabayı gösteriyoruz.
- 🔫 Havuz her zaman [buhar deposu] 'nun en son sürümünü ifade eder (http://store.steampowered.com/app/730/CounterStrike_Global_Offensive).
- ⚠️ Yanlış kullanım durumunda VAC yasaklarından sorumlu değiliz.


## Kredi:
- İnfinityware Geliştirici yazılım grubudur [https://infinityware.tr.ht] Discord [https://discord.gg/94brbZD]
- Ozan Balci [https://github.com/ozanbalci]
- Furkan Balamri [Yok]
- MRX [https://github.com/BurakBalamir]

## İlham Aldımız Kişiler:
- HazeDumper [https://github.com/frk1/hazedumper] 
- BlazeDumper [https://github.com/Akandesh/blazedumper]


