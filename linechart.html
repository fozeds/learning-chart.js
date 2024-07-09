{% set unique_id = chart_id | replace('.', '_') %}
<canvas id="{{ unique_id }}" width="400" height="200"></canvas>
<script>
    let visibleDatasets_{{ unique_id }} = [];

    const ctx_{{ unique_id }} = document.getElementById('{{ unique_id }}').getContext('2d');
    const data_{{ unique_id }} = {
        labels: {{ labels|tojson }},
        datasets: [
            {% for dataset in datasets %}
            {
                label: '{{ dataset.label}}',
                data: {{ dataset.data|tojson }},
                borderColor: '{{ dataset.borderColor }}',
                borderWidth: {{ dataset.borderWidth }},
                fill: {{ dataset.fill|default(false) }},
                backgroundColor: '{{ dataset.backgroundColor|default("rgba(0,0,0,0)") }}',
                tension: {{ dataset.tension|default(0.2) }},
                hidden: true
            }
            {% if not loop.last %},{% endif %}
            {% endfor %}
        ]
    };

    const config_{{ unique_id }} = {
        type: '{{ chart_type|default("line") }}',
        data: data_{{ unique_id }},
        options: {
            responsive: true,
            maintainAspectRatio: false,
            scales: {
                x: {
                    display: true,
                    title: {
                        display: true,
                        text: '{{ x_axis_title|default("Data") }}',
                        font: {
                            size: 14,
                        },
                        color: 'hsla(200,100%,90%,.8)'
                    },
                    ticks: {
                        color: 'hsla(200,100%,90%,.8)'
                    }
                },
                y: {
                    display: true,
                    title: {
                        display: true,
                        text: '{{ y_axis_title|default("Valor") }}',
                        font: {
                            size: 14,
                        },
                        color: 'hsla(200,100%,90%,.8)'
                    },
                    ticks: {
                        color: 'hsla(200,100%,90%,.8)'
                    }
                }
            },
            plugins: {
                title: {
                    display: true,
                    text: '{{ chart_title|default("Meu Gráfico") }}',
                    font: {
                        size: 18,
                    },
                    color: 'hsla(200,100%,90%,.8)'
                },
                legend: {
                    display: true,
                    labels: {
                        usePointStyle: true,
                        color: 'hsla(200,100%,90%,.8)',
                        generateLabels: function(chart) {
                            const original = Chart.defaults.plugins.legend.labels.generateLabels;
                            const labelsOriginal = original.call(this, chart);

                            labelsOriginal.forEach(label => {
                                const index = label.datasetIndex;
                                if (visibleDatasets_{{ unique_id }}.includes(index)) {
                                    label.fillStyle = 'green';
                                } else {
                                    label.fillStyle = 'gray';
                                }
                            });

                            return labelsOriginal;
                        }
                    },
                    onClick: function(e, legendItem, legend) {
                        const index = legendItem.datasetIndex;
                        const ci = legend.chart;
                        const isVisible = ci.isDatasetVisible(index);

                        ci.setDatasetVisibility(index, !isVisible);
                        ci.update();

                        if (isVisible) {
                            visibleDatasets_{{ unique_id }} = visibleDatasets_{{ unique_id }}.filter(idx => idx !== index);
                        } else {
                            visibleDatasets_{{ unique_id }}.push(index);
                        }

                        legend.legendItems[index].fillStyle = isVisible ? 'gray' : 'green';
                        ci.legend.update();
                    }
                }
            }
        },
        plugins: [{
            id: 'removeStrikethrough',
            afterUpdate: function(chart) {
                const originalFillText = chart.ctx.fillText;
                chart.ctx.fillText = function(text, x, y, maxWidth) {
                    originalFillText.apply(this, arguments);
                    this.fillStyle = "rgba(0,0,0,0)";
                };
            }
        }, {
            id: 'dataLabels',
            afterDatasetsDraw: function(chart) {
                const ctx = chart.ctx;
                chart.data.datasets.forEach((dataset, i) => {
                    const meta = chart.getDatasetMeta(i);
                    if (!chart.isDatasetVisible(i)) return;

                    meta.data.forEach((element, index) => {
                        ctx.fillStyle = 'hsla(200,100%,90%,.8)'; 
                        const fontSize = 12;
                        const fontStyle = 'normal';
                        const fontFamily = 'Helvetica Neue';
                        ctx.font = Chart.helpers.fontString(fontSize, fontStyle, fontFamily);

                        const dataString = dataset.data[index].toFixed(2).toString();

                        ctx.textAlign = 'center';
                        ctx.textBaseline = 'middle';

                        const padding = 5;
                        const position = element.tooltipPosition();
                        ctx.fillText(dataString, position.x, position.y - (fontSize / 2) - padding);
                    });
                });
            }
        }]
    };

    new Chart(ctx_{{ unique_id }}, config_{{ unique_id }});
</script>
