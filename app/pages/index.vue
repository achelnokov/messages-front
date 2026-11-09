<template>
    <div class="page-section active">

      <!-- Stat Cards -->
      <div class="grid-6" style="margin-bottom:24px;">
        <div class="stat-card info">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;">
            <div>
              <div class="stat-label">Всего сообщений</div>
              <div class="stat-value">124</div>
            </div>
            <div class="stat-icon">
                <Icon name="solar:chat-round-dots-bold-duotone" size="20" />
            </div>
          </div>
          <div class="trend up">
            +12 за последнюю неделю
          </div>
        </div>

        <div class="stat-card success">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;">
            <div>
              <div class="stat-label">Активных проектов</div>
              <div class="stat-value">40</div>
            </div>
            <div class="stat-icon">
                <Icon name="solar:kanban-line-duotone" size="20" />
            </div>
          </div>
          <div class="trend up hidden">
           
          </div>
        </div>

        <div class="stat-card info">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;">
            <div>
              <div class="stat-label">Активных операторов</div>
              <div class="stat-value">56</div>
            </div>
            <div class="stat-icon">
                <Icon name="solar:user-rounded-bold-duotone" size="20" />
            </div>
          </div>
          <div class="trend up">
            +23% за неделю
          </div>
        </div>

        <div class="stat-card success">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;">
            <div>
              <div class="stat-label">Успешных сделок</div>
              <div class="stat-value">903</div>
            </div>
            <div class="stat-icon">
                <Icon name="solar:graph-up-line-duotone" size="20" />
            </div>
          </div>
          <div class="trend up">
            +18% за неделю
          </div>
        </div>

        <div class="stat-card ">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;">
            <div>
              <div class="stat-label">Незавершенных сделок</div>
              <div class="stat-value">1008</div>
            </div>
            <div class="stat-icon">
                <Icon name="solar:graph-down-line-duotone" size="20" />
            </div>
          </div>
          <div class="trend warn">
            
          </div>
        </div>

        <div class="stat-card info">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;">
            <div>
              <div class="stat-label">Отдано сообщений</div>
              <div class="stat-value">1,240</div>
            </div>
            <div class="stat-icon">
            </div>
          </div>
          <div class="trend up">
            
          </div>
        </div>
      </div>

<div class="grid-3" style="margin-bottom:24px;">
        <!-- Activity Timeline -->
        <div class="card hidden">
          <div class="section-header">
            <div>
              <div class="section-title">Aktivitas Terkini</div>
              <div class="section-sub">Real-time updates</div>
            </div>
            <button class="btn btn-outline btn-sm">Semua</button>
          </div>
          <div class="timeline">
            <div class="timeline-item">
              <div class="timeline-dot">
                <iconify-icon icon="solar:bag-bold" style="font-size:14px;"></iconify-icon>
              </div>
              <div class="timeline-content">
                <strong>Produk Kemeja Karawo ditambahkan</strong>
                <span>5 menit lalu · Oleh Admin</span>
              </div>
            </div>
            <div class="timeline-item">
              <div class="timeline-dot success">
                <iconify-icon icon="solar:cart-check-bold" style="font-size:14px;"></iconify-icon>
              </div>
              <div class="timeline-content">
                <strong>Pesanan #INV-001 dikonfirmasi</strong>
                <span>15 menit lalu</span>
              </div>
            </div>
            <div class="timeline-item">
              <div class="timeline-dot warning">
                <iconify-icon icon="solar:box-bold" style="font-size:14px;"></iconify-icon>
              </div>
              <div class="timeline-content">
                <strong>Stok benang sulaman menipis</strong>
                <span>1 jam lalu · Perlu tindakan</span>
              </div>
            </div>
            <div class="timeline-item">
              <div class="timeline-dot info">
                <iconify-icon icon="solar:user-plus-bold" style="font-size:14px;"></iconify-icon>
              </div>
              <div class="timeline-content">
                <strong>Perajin baru: Ibu Siti bergabung</strong>
                <span>3 jam lalu · Wilayah Bone Bolango</span>
              </div>
            </div>
            <div class="timeline-item">
              <div class="timeline-dot">
                <iconify-icon icon="solar:notes-bold" style="font-size:14px;"></iconify-icon>
              </div>
              <div class="timeline-content">
                <strong>Artikel "Karawo Warisan Gorontalo" dipublish</strong>
                <span>5 jam lalu</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Top Products -->
        <div class="card hidden">
          <div class="section-header">
            <div>
              <div class="section-title">Produk Terlaris</div>
              <div class="section-sub">Bulan ini</div>
            </div>
          </div>
          <div class="product-rank">
            <div class="rank-item">
              <div class="rank-num">1</div>
              <div style="flex:1;">
                <div style="font-size:0.875rem;font-weight:600;color:var(--text);">Kemeja Karawo Premium</div>
                <div style="font-size:0.75rem;color:var(--text-light);">24 terjual · Rp 8.400.000</div>
              </div>
              <div class="badge-pill badge-active">+12%</div>
            </div>
            <div class="rank-item">
              <div class="rank-num silver">2</div>
              <div style="flex:1;">
                <div style="font-size:0.875rem;font-weight:600;color:var(--text);">Selendang Motif Padi</div>
                <div style="font-size:0.75rem;color:var(--text-light);">18 terjual · Rp 5.400.000</div>
              </div>
              <div class="badge-pill badge-active">+8%</div>
            </div>
            <div class="rank-item">
              <div class="rank-num bronze">3</div>
              <div style="flex:1;">
                <div style="font-size:0.875rem;font-weight:600;color:var(--text);">Blouse Karawo Elegan</div>
                <div style="font-size:0.75rem;color:var(--text-light);">15 terjual · Rp 6.750.000</div>
              </div>
              <div class="badge-pill badge-active">+5%</div>
            </div>
            <div class="rank-item">
              <div class="rank-num" style="background:var(--text-light);">4</div>
              <div style="flex:1;">
                <div style="font-size:0.875rem;font-weight:600;color:var(--text);">Tas Tangan Karawo</div>
                <div style="font-size:0.75rem;color:var(--text-light);">12 terjual · Rp 3.600.000</div>
              </div>
              <div class="badge-pill badge-gray">+2%</div>
            </div>
            <div class="rank-item">
              <div class="rank-num" style="background:var(--text-light);">5</div>
              <div style="flex:1;">
                <div style="font-size:0.875rem;font-weight:600;color:var(--text);">Sarung Karawo Tradisional</div>
                <div style="font-size:0.75rem;color:var(--text-light);">10 terjual · Rp 4.500.000</div>
              </div>
              <div class="badge-pill badge-gray">-1%</div>
            </div>
          </div>
        </div>

        <!-- Stock Alert -->
        <div class="card" v-for="n in 3" :key="n">
          <div class="section-header">
            <div>
              <div class="section-title">Худшие показатели</div>
              <div class="section-sub">Статистика по операторам</div>
            </div>
          </div>
          <div class="stock-alert">
            <div class="alert-item">
              <div class="name">Вениамин Помидоров</div>
              <div style="font-size:0.75rem;font-weight:700;color:var(--danger);">15 отказов</div>
            </div>
            <div class="alert-item">
              <div class="name">Антон Палыч</div>
              <div style="font-size:0.75rem;font-weight:700;color:var(--warning);">280 незавершенных</div>
            </div>
            <div class="alert-item">
              <div class="name">Светозар Иванов</div>
              <div style="font-size:0.75rem;font-weight:700;color:var(--warning);">30 незавершенных</div>
            </div>
            <div class="alert-item">
              <div class="name">Джон Смит</div>
              <div style="font-size:0.75rem;font-weight:700;color:var(--danger);">недостаточно хорош</div>
            </div>
            <div class="alert-item">
              <div class="name">Анатолий Новосельцев</div>
              <div style="font-size:0.75rem;font-weight:700;color:var(--warning);">робкий и застенчивый</div>
            </div>
          </div>
          <button class="btn btn-warning btn-sm" style="margin-top:14px;width:100%;justify-content:center;">
            Вся статистика
          </button>
        </div>
      </div>
    </div>
</template>