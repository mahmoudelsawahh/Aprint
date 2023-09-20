<div className="row">
                                                      {e.childrens.map((item)=>{
                                              return (
                                                <div key={item.id} className="col-6">
                                                  {/* -------------------------------------- */}
                                              <div style={{textAlign : 'center'}}
                                                onClick={() => {
                                                  const Option_data = {
                                                    section_id: parseFloat(
                                                      item.section_id
                                                    ),
                                                    Option_id: parseFloat(item.id),
                                                  };
                                                  if (
                                                    selected_op.indexOf(
                                                      Option_data
                                                    ) === -1
                                                  ) {
                                                    const old_selected = selected_op.filter(
                                                      (op) =>
                                                        parseFloat(
                                                          op.section_id
                                                        ) !==
                                                        parseFloat(item.section_id)
                                                    );
                                                    const New_selected = [
                                                      ...old_selected,
                                                      Option_data,
                                                    ];
                                                    setSelected(New_selected);

                                                    if (All_ids.length <= 0) {
                                                      dispatch(
                                                        getProductSummery(
                                                          `?product_id=${id2}&options[0]=${parseFloat(
                                                            item.id
                                                          )}&width=${width}&height=${height}&quantity=${quantity}`
                                                        )
                                                      );
                                                    } else {
                                                      // SendData();
                                                      SendDataOption(
                                                        New_selected
                                                      );
                                                    }
                                                  }
                                                }}
                                              >
                                                {item.image ? (
                                                  <>
                                                    <div
                                                      className="Card_Image"
                                                      style={{
                                                        borderColor: All_ids.includes(
                                                          item.id
                                                        )
                                                          ? "#0a3565"
                                                          : "#d1d1d1",
                                                      }}
                                                      
                                                    >
                                                        <img
                                                          src={item.image}
                                                          alt=""
                                                          width={100} height={100}
                                                        />
                                                      </div>
                                                      
                                                      <h3>{item.name}</h3>
                                                  
                                                  </>
                                                ) : (
                                                  <>
                                                    <div
                                                      className="Chose text-center "
                                                      style={{
                                                        borderColor: All_ids.includes(
                                                          item.id
                                                        )
                                                          ? "#0a3565"
                                                          : "#d1d1d1",
                                                      }}
                                                    >
                                                      {item.name}
                                                    </div>
                                                    <p>{item.description}</p>
                                                  </>
                                                )}
                                              </div>
                                                  {/* -------------------------------------- */}
                                                </div>
                                              )
                                            })}
                                                      </div>